---
title: "eGalax Touch controller via FTDI USB-UART"
date: 2011-06-03
forum: Hardware
---

### Post by Turifuzz on 2011-06-03
I've been trying to get my touch screen working in Ubuntu 11.04 with a custom made hardware. The touch controller is a common eGalax 4-wire RS-232 model and I've installed the drivers and calibration tool per this thread: [http://forum.eeeuser.com/viewtopic.php?pid=363668](http://forum.eeeuser.com/viewtopic.php?pid=363668)
 
However, my problem seems to be that I don't have any real serial ports, but they are implemented with FTDI's FT4232H chip - four ports from single USB line. The port used for the controller is /dev/ttyUSB2, which is put to xorg.conf Input Device section. eGalaxTouch gives only an error message "No touch controller found." with no additional info, where to start now?
 
Controller itself is working, I'm getting pulses to oscilloscope from TX line when tapping the screen. Also the first FTDI output, ttyUSB0, is constantly used for terminal, so this is clearly just a matter of recognizing the controller in Ubuntu.

---

### Post by Turifuzz on 2011-06-06
The controller now gives gibberish to minicom when the screen is pressed, but xinput-calibrator or eGalaxTouch still can not find the controller for calibration. Where do I have to put the data about ttyUSB2 to make the touch screen visible to X?

---

