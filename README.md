# 🚀 Dotfile Configuration

Bộ sưu tập cấu hình Linux (Dotfiles) hoàn chỉnh cho shell, terminal, và các công cụ hệ thống.

## 📁 Cấu Trúc Repository

```
dotfile/
├── fish/                    # Cấu hình Fish Shell
│   ├── config.fish         # Fish shell configuration
│   └── fish_variables      # Fish variables and environment
├── kitty/                  # Cấu hình Kitty Terminal
│   ├── kitty.conf          # Kitty terminal configuration
│   └── kitty.conf.save     # Backup configuration
├── fastfetch/              # Cấu hình Fastfetch (System Info)
│   ├── config.jsonc        # Fastfetch configuration
│   ├── ascii/              # ASCII art files
│   ├── images/             # System images
│   ├── pngs/               # PNG graphics
│   └── README.md           # Fastfetch documentation
├── astronaut/              # GRUB Boot Theme "Astronaut"
│   ├── theme.txt           # GRUB theme configuration
│   ├── JetBrainsMono_*.pf2 # Font files for GRUB
│   ├── background.png      # Boot screen background
│   └── icons/              # Boot menu icons
├── starship.toml           # Starship prompt configuration
├── background              # Wallpaper (8.4MB)
└── astronaut.png           # Preview image

```

## 📦 Ứng Dụng Cần Cài Đặt

### 1. **Shell & Terminal**
```bash
# Fish Shell (Modern shell tương tác)
sudo pacman -S fish        # Arch Linux
sudo apt install fish      # Ubuntu/Debian
brew install fish          # macOS

# Kitty (GPU-based terminal)
sudo pacman -S kitty       # Arch Linux
sudo apt install kitty     # Ubuntu/Debian
brew install kitty         # macOS
```

### 2. **Prompts & System Info**
```bash
# Starship (Cross-shell prompt)
curl -sS https://starship.rs/install.sh | sh

# Fastfetch (Fast system information display)
sudo pacman -S fastfetch   # Arch Linux
sudo apt install fastfetch # Ubuntu/Debian
brew install fastfetch     # macOS
```

### 3. **Fonts - Microsoft và Powerline**

#### Fonts Cần Thiết
```bash
# JetBrains Mono (sử dụng trong config)
sudo pacman -S ttf-jetbrains-mono       # Arch Linux
sudo apt install fonts-jetbrains-mono   # Ubuntu/Debian
brew install font-jetbrains-mono        # macOS

# Microsoft Fonts (tùy chọn - bạn yêu cầu)
sudo pacman -S ttf-ms-fonts             # Arch Linux

# Ubuntu/Debian - Cài đặt Microsoft Fonts từ source
sudo apt update
sudo apt install -y cabextract xfonts-encodings xfonts-utils fonts-liberation

# Download và cài đặt
cd /tmp
wget https://sourceforge.net/projects/corefonts/files/latest/download -O msfonts.tar.gz
tar -xzf msfonts.tar.gz
mkdir -p ~/.local/share/fonts/microsoft
cp *.ttf ~/.local/share/fonts/microsoft/
fc-cache -f -v

# Hoặc sử dụng package đã chuẩn bị sẵn
sudo apt install ttf-mscorefonts-installer

# Powerline Fonts (cho terminal symbols)
git clone https://github.com/powerline/fonts.git --depth=1
cd fonts
./install.sh
cd .. && rm -rf fonts

# Nerd Fonts (tích hợp biểu tượng)
sudo pacman -S nerd-fonts   # Arch Linux
# macOS
brew tap homebrew/cask-fonts
brew install font-meslo-lg-nerd-font

# Hoặc download từ: https://www.nerdfonts.com/font-downloads
```

## 🔧 Cài Đặt & Sử Dụng

### 1. **Clone Repository**
```bash
git clone https://github.com/xuannhat1503/dotfile ~/.config/dotfiles
cd ~/.config/dotfiles
```

### 2. **Cấu Hình Fish Shell**
```bash
# Copy config Fish
mkdir -p ~/.config/fish
cp fish/config.fish ~/.config/fish/
cp fish/fish_variables ~/.config/fish/

# Set Fish làm default shell
chsh -s /usr/bin/fish

# Hoặc từ bash
echo /usr/bin/fish | sudo tee -a /etc/shells
chsh -s /usr/bin/fish
```

### 3. **Cấu Hình Kitty Terminal**
```bash
# Copy config Kitty
mkdir -p ~/.config/kitty
cp kitty/kitty.conf ~/.config/kitty/

# Restart Kitty hoặc reload config: Ctrl+Shift+F5
```

### 4. **Cấu Hình Starship Prompt**
```bash
# Copy config Starship
mkdir -p ~/.config
cp starship.toml ~/.config/

# Add to shell config (Fish):
echo 'starship init fish | source' >> ~/.config/fish/config.fish

# Add to bash/zsh:
echo 'eval "$(starship init bash)"' >> ~/.bashrc
```

### 5. **Cấu Hình Fastfetch**
```bash
# Copy config
mkdir -p ~/.config/fastfetch
cp -r fastfetch/* ~/.config/fastfetch/

# Chạy fastfetch
fastfetch

# Hoặc thêm vào shell config để hiển thị khi mở terminal
echo 'fastfetch' >> ~/.config/fish/config.fish
```

### 6. **Cài Đặt GRUB Theme (Astronaut)**
```bash
# Backup GRUB config hiện tại
sudo cp /etc/default/grub /etc/default/grub.backup

# Copy theme vào thư mục GRUB
sudo mkdir -p /boot/grub/themes/astronaut
sudo cp -r astronaut/* /boot/grub/themes/astronaut/

# Copy background
sudo cp background /boot/grub/themes/astronaut/

# Chỉnh sửa GRUB config
sudo nano /etc/default/grub

# Thêm/Sửa dòng:
# GRUB_THEME="/boot/grub/themes/astronaut/theme.txt"
# GRUB_GFXMODE=1920x1080x32

# Cập nhật GRUB
sudo grub-mkconfig -o /boot/grub/grub.cfg

# Hoặc trên UEFI:
sudo grub-mkconfig -o /boot/efi/EFI/grub/grub.cfg
```

## 🎨 Tùy Chỉnh Cấu Hình

### Starship Prompt
Chỉnh sửa `starship.toml` để tùy chỉnh:
- Biểu tượng OS
- Màu sắc
- Định dạng thông tin (git, language, etc.)

### Kitty Terminal
Chỉnh sửa `kitty/kitty.conf`:
```conf
# Font
font_family JetBrains Mono
font_size 12

# Theme colors
background #1e1e2e
foreground #cdd6f4
```

### Fish Config
Chỉnh sửa `fish/config.fish`:
- Aliases
- Functions
- Environment variables

### Fastfetch
Chỉnh sửa `fastfetch/config.jsonc`:
- Output format
- Modules hiển thị
- Custom ASCII art

## 🔤 Font Recommendations

| Font | Mục Đích | Cài Đặt |
|------|----------|--------|
| **JetBrains Mono** | Terminal, GRUB | `ttf-jetbrains-mono` |
| **Nerd Font** | Powerline symbols | `nerd-fonts` |
| **Microsoft Fonts** | Tương thích Windows | `ttf-ms-fonts` |
| **Liberation** | Open Sans alternative | `fonts-liberation` |
| **DejaVu** | Unicode support | `ttf-dejavu` |

## 🐛 Troubleshooting

### GRUB Theme không hiển thị
```bash
# Kiểm tra quyền truy cập
ls -la /boot/grub/themes/astronaut/

# Kiểm tra GRUB config
grep GRUB_THEME /etc/default/grub

# Tạo lại GRUB config
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

### Kitty không nhận font
```bash
# Kiểm tra font có sẵn
kitty list-fonts

# Cài lại font
fc-cache -f -v
```

### Fish Shell không chạy
```bash
# Kiểm tra cài đặt
which fish

# Thêm vào /etc/shells nếu cần
echo /usr/bin/fish | sudo tee -a /etc/shells
```

### Starship prompt không hiển thị biểu tượng
- Đảm bảo terminal sử dụng Nerd Font
- Kiểm tra config: `starship config`
- Update Starship: `starship self-update`

## 📱 Preview

- **Terminal**: Kitty + Fish Shell + Starship
- **System Info**: Fastfetch with custom ASCII art
- **Boot Menu**: Astronaut GRUB theme
- **Background**: Wallpaper included (8.4MB)

## 📚 Tài Liệu Tham Khảo

- [Fish Shell](https://fishshell.com)
- [Kitty Terminal](https://sw.kovidgoyal.net/kitty/)
- [Starship Prompt](https://starship.rs)
- [Fastfetch](https://github.com/fastfetch-cli/fastfetch)
- [GRUB Theming](https://www.gnu.org/software/grub/manual/grub/html_node/Theme-format.html)
- [Nerd Fonts](https://www.nerdfonts.com)

## ⚙️ Hệ Thống Được Hỗ Trợ

- 🐧 **Arch Linux** (Pacman)
- 🔵 **Ubuntu/Debian** (Apt)
- 🍎 **macOS** (Homebrew)
- Các distro khác (cần điều chỉnh package manager)

## 📝 License

Các cấu hình này có thể được sử dụng và tùy chỉnh tự do cho mục đích cá nhân.

---

**Last Updated:** 2024
**Maintained by:** xuannhat1503
