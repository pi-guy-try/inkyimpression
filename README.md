# Inky Impression 13.3 Display Tools

Python tools and scripts for displaying custom images and slideshows on the Pimoroni Inky Impression 13.3" e-paper display with Raspberry Pi Zero 2W, including Samba integration and automated image formatting.

While Pimoroni's out of the box code is fantastic, it leaves it up to the user to edit the photos to make them look good. So these scripts will:

A) auto format your images to look good on the inky. Horizontal photos have the ratio fixed, ex a 6000x4000 photo will be cropped to 5333x4000 image based on the center of the image. If horizontal images are too short, it will letterbox the imgaes. Vertical images are pillarboxed based on the size of the image. All Images are then scaled down to 1600 x 1200 pixels. This makes images natively ready for the Impression and also saves on storage space. 

B) Choose a manual photo to display. You can select the saturation as well. Personally, I use it for my favorite photos and use the RaspController mobile app to change. 

C) Cycle through a random photo. Best paired with a cronjob. 

If this is your first time using a Inky Impression, follow the Pimoroni [Pimoroni Getting Started Guide](https://learn.pimoroni.com/article/getting-started-with-inky-impression)

---

## Features

- **Automatic image formatting** for the Inky Impression’s 4:3 color display
- **Slideshow mode** and **manual image display**
- **Samba network share integration** for displaying photos from NAS or other devices
- Easy setup and cross-platform Python scripts
- Uses the latest [Pimoroni Inky drivers](https://github.com/pimoroni/inky)

---

## Hardware Requirements

- **Pimoroni Inky Impression 13.3"** e-paper display
- **Raspberry Pi Zero 2W** (or any compatible Pi)
- (Optional) Networked storage (e.g., Samba server/NAS)

---

## Software Requirements

- Python 3.8+
- Pip

---

## Installation

1. **Clone this repository:**
    ```sh
    git clone https://github.com/your-username/inky-impression-tools.git
    cd inky-impression-tools
    ```

2. **Install dependencies:**
    ```sh
    pip install -r requirements.txt
    ```
    This will install:
    - Pillow (for image processing)
    - smbprotocol (for Samba network shares)
    - The latest Inky drivers from Pimoroni’s GitHub

3. **Enable and configure Samba/network access** if you wish to pull images from a NAS.
    This will make it easy to upload your photos to the raspberry pi from your computer:
    - Pillow (for image processing)


4. **(Optional but recommended) Create a Python virtual environment:**
    ```sh
    python3 -m venv venv-inky
    source venv-inky/bin/activate
    ```
5. **(Optional) Make a shortcut/alias for activating your virtual environment:**

    - On **Linux**, add the following to your `~/.bashrc` or `~/.zshrc`:
      ```sh
      alias inkyenv='source /full/path/to/inky-impression-tools/venv-inky/bin/activate'
      ```
      Now you can type `inkyenv` in any terminal to activate it.

      Pro Tip: to run from the command line with the manual_photo
---

## Usage

### 1. `manualphoto.py`
Display a single photo, formatted to fit your Inky Impression.

```sh
python manualphoto.py --file path/to/photo.jpg --saturation 0.85
```
- Automatically resizes and formats the image for optimal display.

### 2. `inky_slideshow.py`
Display a slideshow of images from a folder.

```sh
python inky_slideshow.py --folder path/to/image_folder --saturation 0.85
```
- Rotates through all images, formatting each for the display.

### 3. `inky_formatter.py`
Fetch and format images from a Samba network share for display.

```sh
python samba_inky_formatter.py --samba-path //your-nas/photos --username youruser --password yourpass
```
- Mounts the share, fetches images, formats, and displays them on the Inky.

---

## Example

You can find example scripts and sample images in the `examples/` folder.

---

## Troubleshooting

- Make sure your user is in the `i2c` and `spi` groups if using the Inky Impression on Raspberry Pi.
- For SMB/network issues, ensure your NAS credentials and paths are correct.
- For display errors, check cabling and install the latest [Pimoroni Inky drivers](https://github.com/pimoroni/inky).

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

## Credits

- [Pimoroni Inky](https://github.com/pimoroni/inky)
- [Pimoroni Getting Started Guide](https://learn.pimoroni.com/article/getting-started-with-inky-impression)
- Inspired by projects in the Raspberry Pi and e-paper display community.
