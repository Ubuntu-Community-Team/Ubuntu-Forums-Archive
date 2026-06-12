---
title: "Costom udev rules no longer work."
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by chrestomanci on 2007-05-09
Hello

I my old Ubuntu 6.10 setup, I had created a costom udev rules file for my various USB devices, so that they always mounted at the same mount points. My rules file looks like this:

# 1Gb Blue Pill thumb drive
BUS="usb", SYSFS{serial}="0AE0756111A09A65", NAME="bluepill"

# Silver 40Gb USB hard drive enclosure
BUS="usb", SYSFS{serial}="DEF108F34B29", NAME="silver40Gb"

# Nikon D70 Camera
BUS="usb", SYSFS{product}=="NIKON DSC D70" NAME="Nikon-D70"

Anyway, since upgrading to 7.04, it no longer works. There are a bunch of errors about the file on boot up, and when I insert a USB storage device the system creates a mount point based on the drive name with a numeral appended. I have a bunch of scripts that rely on the name being consistent, so those appended numbers are screwing things up.

Does anyone know how to get things back the way they where before?

Thanks.

---

### Post by Ken_Lewis81 on 2007-05-11
Can you post the dmesg log output as to what those errors are?  Have you filed a bug against the upgrade?

Take care.
Ken.

---

