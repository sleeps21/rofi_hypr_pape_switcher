# Wallpaper Selector Script

The script enables to switch the wallpaper on all connected monitors using rofi and hyprctl.

## Usage

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/rofi_hypr_pape_switcher.git
    cd rofi_hypr_pape_switcher
    ```

2. Make the script executable:
    ```bash
    chmod +x rofi_select_wallpaper.sh
    ```
3. Ensure you have a directory named `wallpaper` in your home directory and place your wallpaper images there: 
```bash
mkdir -p ~/wallpaper 
``` 
	Place your images in this directory. 
```bash
mv /path/to/your/images/* ~/wallpaper/ 
```
4. Run the script:
    ```bash
    ./rofi_select_wallpaper.sh
    ```
5. (Optional) Add Keybinding
```bash
bind = $mainMod SHIFT, P, exec, $HOME/.config/rofi/rofi_select_wallpaper.sh
```

## Requirements
#### Rofi 
For installation instructions for Rofi, refer to the [official Rofi installation guide](https://github.com/davatorium/rofi/blob/next/INSTALL.md).
#### Hyprland and Hyprctl 
To install Hyprland and hyprctl, follow the instructions on the [Hyprland GitHub repository](https://github.com/vaxerski/Hyprland).

## Script Details
1. **Builds a List of Wallpapers**: The script scans scans the wallpaper directory (`~/wallpaper`) and collects all filenames. These filenames are then passed to Rofi, which displays a menu for you to select your desired wallpaper.
    
2. **Retrieves all Connected Monitors**: The script retrieves a list of all connected monitors to ensure that the selected wallpaper is applied to each one.
    
3. **Sets the Wallpaper Using Hyprctl**:
    
    - **Unload Preloaded Wallpapers**: The script first unloads all currently preloaded wallpapers using `hyprctl hyprpaper unload all`.
    - **Preload the Selected Wallpaper**: It then preloads the selected wallpaper using `hyprctl hyprpaper preload`.
    - **Apply the Wallpaper to Each Monitor**: The script loops through every detected monitor and sets the selected wallpaper on each one using `hyprctl hyprpaper wallpaper`.

### Important Note 
Ensure that `hyprpaper` is already running before executing the script.
