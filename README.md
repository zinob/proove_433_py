Controll 433 mhz sockets Nexa/Proove/Koppla via RPI TX

This program is ~~a bastardisation~~ continuation of https://github.com/atus/proove_433_py

It uses the [rpi-tx](https://github.com/F5OEO/rpitx) to bit-bang a port fast enough to create a 443 signal, which means that as long as you are OK with the range being rahter short you can remote-control any device compatible with the old nexa/proove standard by just adding an 15-ish cm areal to GPIO 4 of a raspberry pi. You should allso add a band pass filter both to improve range and to avoid potentially **illegal radiofrequency interference** due to the terrible harmonics of this transmission system.  

This relies on rpi-tx being installed on the pie and being globally availible since I litteraly took the easiest to bastardize implementation i could find of the Nexa protocol and tacked a call to the `sendook` progam on via `subprocess`.

## Known issues
* The controller ID is curently hard-coded, Il'l change that some time, maybe...
* The code-quality is "not great"
* Dimming is currently not supported and might never be since it was not in the original library and it depends on wether or not i can be bothered to figure out/find the protocol for that.

## Usage:
* Make sure you have installed and configured [rpitx](https://github.com/F5OEO/rpitx) 
* Make sure you have an areal/antenna on [GPIO4 of the raspberry pi] https://pinout.xyz/pinout/pin7_gpio4/
* To simulate pressing button 1 on a controller use: `sudo python proove.py  --id 0 --on` for everything else use `proove.py --help`

![a raspberry pie with a questionable antenna](./rpi.jpg)
