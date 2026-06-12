---
title: "HP LJ4 Problem"
date: 2010-05-02
forum: Hardware
---

### Post by merlinus on 2010-05-02
I have an HP Laserjet 4 that I use with a parallel-to-USB cable.  It worked fine in 9.10, and before that as well.

With installation of 10.04, however, I cannot get it to work.  lsusb lists the cable when the printer is turned on, but in the Add Printer dialog, I can only select Other, and then need to enter a device URI.  I have tried just about all options, including

usb:/dev/lp0 and usb://dev/lp0

to no avail.

I have also tried a different cable, and although it also showed up in lsusb, it did not work.

Any ideas?

Many thanks!

---

### Post by merlinus on 2010-05-05
I got the printer to work on a dual-boot Win 2000 machine, so clearly this is an Ubuntu problem, and not the cable nor printer.

I installed the Linux driver from HP, and  this did not show any USB printer, and manually entering the USB:device code did not work either.

Any suggestions would be greatly appreciated!

---

### Post by merlinus on 2010-05-06
In case anyone has this problem, here is how I solved it:

1. Select System/Admin/Printing from the menu.
2. Press New and when the dialogue box comes up for New Printer press forward and then select your printer (HP LJ4 in my case). I know this will not be for a USB connection but we'll fix that later.
3. Once you have selected your printer driver press Apply and when asked if you want to print a test page select No.
4. Now you have your printer driver installed and should see it in the Printer Configuration window. Right-click on it and select properties.
5. Change the Device URI to parallel:/dev/usb/lp0 and press Apply.
6. Print a Test Page to make sure it is working.

---

