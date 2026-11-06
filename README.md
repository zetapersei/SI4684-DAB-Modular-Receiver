[![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/PE5PVB/TEF-Nextion-Multiband#contributing)
[![License](https://img.shields.io/badge/license%20-%20GNU_GPLv3-GPLv3?color=blue)](https://github.com/PE5PVB/TEF-Nextion-Multiband/blob/main/LICENSE)

# Note:
The version in the repository is an ongoing development. It could and will contain bugs. To make sure you use the latest fully tested firmware, check the releases!

# SI4684 DAB receiver
Advanced DAB Tuner software for Skyworks SI4684 tuner with ESP32 board and a color LCD\
More information: https://www.pe5pvb.nl/

## Fork updates

### Modular receiver PCB
This fork adds a KiCad redesign for the **DAB+ receiver module A**. The board keeps the SI4684 tuner, 19.2 MHz reference, RF matching network, SMA antenna connector, and 1.8 V / 3.3 V regulation together as a dedicated receiver module. Its separate headers expose power, SPI, digital audio/control, and analog audio connections so the tuner can be integrated with the controller, display, and audio sections as distinct modules.

The KiCad source and reference outputs are in [`Kicad/`](Kicad/):
- `Dab+.kicad_sch` and `Dab+.kicad_pcb`: schematic and two-layer PCB.
- `schematic.pdf` and `layout.pdf`: exported design drawings.
- `Dab_bom.xlsx` and `BOM/`: bill of materials and component references.

Check the schematic for the exact connector pinout before wiring the modules: J1–J6 serve different signal groups, including the power rails (J3) and stereo analog output (J4). Do not assume the headers are interchangeable.

The checked-in `Dab+.csv` does not match this PCB revision (including connector and U3 details). Regenerate it from the current schematic and verify the U3 supplier part number before ordering components.

### Firmware modules
The firmware in `src/` is organized around the same functional boundaries:
- `si4684.*`: tuner control, DAB service data, and MOT slideshow reception.
- `comms.*`: serial command and status protocol.
- `gui.*`, `graphics.h`, `font.h`, and `language.h`: display, graphics, fonts, and localization.
- `slideshow.*` and `JPEGdecoder.*`: slideshow rendering.
- `IRReceiver.*` and `TPA6130A2.*`: remote input and headphone amplifier.




# Libraries
These are the libraries used for this project:
- https://github.com/Bodmer/TFT_eSPI
- https://github.com/Bodmer/JPEGDecoder
- https://github.com/bitbank2/PNGdec

Use these settings in the TFT_eSPI library:
```
#define ILI9341_DRIVER
#define TFT_CS          5
#define TFT_DC          4
#define TFT_RST         17
#define SPI_FREQUENCY   50000000
#define SMOOTH_FONT
```
# Buttons
A brief instruction for the buttons:
- Top encoder: Choose frequency or memory channel
- Bottom encoder: Choose service or set headphones volume
- Top button: Short press: Service information, Long press: Stand-by mode.
- Middle button: Short press: Set mode, Long press: Open menu.
- Lower button: Toggle Slideshow view.
  
## Contributing
I'm open for a new ideas in our project. Feel free to share your thoughts in [Discussions](https://github.com/PE5PVB/SI4684-DAB-Receiver/discussions).\
You can also contribute your own code using [Pull Requests](https://github.com/PE5PVB/SI4684-DAB-Receiver/pulls). We will review it and merge into main branch.

You are using my software and you found a difficulty? Please create new [issue](https://github.com/PE5PVB/SI4684-DAB-Receiver/issues) and describe your problem.

I also would like to invite you to join our Discord community where we share our ideas and help each other with some issues.\
[<img alt="Join the TEF6686 Discord community!" src="https://i.imgur.com/lI9Tuxf.png" height="120">](https://discord.gg/ZAVNdS74mC)  

Special thanks to all [contributors](https://github.com/PE5PVB/TEF-Nextion-Multiband/graphs/contributors). You are awesome! ❤️
## License
This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details. 

## If you like this software
<a href="https://www.buymeacoffee.com/pe5pvb"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a coffee&emoji=☕&slug=pe5pvb&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff" /></a>
