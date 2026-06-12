---
title: "toughbook cf-30 touchscreen calibration"
date: 2009-04-17
forum: Hardware
---

### Post by uglyoldbob on 2009-04-17
I am not sure if this is in the right place.

I have a panasonic toughbook cf-30. I upgraded from 8.04 to 8.10 recently (format and install method). I was using the evtouch driver for my touchscreen and I expected to have to redo the setup for that after the install. However after installing, I notice that the touchscreen works (although is not calibrated). I scanned the /etc/X11/xorg.conf, but I didn't find anything related to a touchscreen driver (it is almost empty). Lsmod tells me that the evdev module is loaded. I think that this MAY be the driver being used for the touchscreen, but I don't know how to confirm this. I am at a lost for where to look next.

---

### Post by torstenaf on 2011-04-17
Quick and dirty way to calibrate that works for me...

Go to the website and download .deb file for xinput_calibrator and install. Run the program xinput_calibrator from the command line, and follow the instruction. 

1. Run xinput_calibrator
2. Click or tap on four points
3. Look at the command line output.
4. Create a file as specified in the terminal window.
5. Copy contents of file as specified in the terminal window into new file
6. Reboot.
7. Enjoy calibrated screen.

---

### Post by flipjarg on 2011-06-06
Super easy! I just did it for my Toughbook CF-29 in Ubuntu. This probably would work for Debian as well... without any manual configuration I had pretty much the same functionality in Debian and Ubuntu right of the bat.

---

### Post by gowyn on 2012-06-07
just trying this.  Completely new to Ubuntu and terminal.  I typed this:  /home/mynamehere/Downloads/xinput-calibrator_0.7.5-1ubuntu1_i386.deb and got permission denied message.

Did I download the wrong file or what am I doing wrong?

---

