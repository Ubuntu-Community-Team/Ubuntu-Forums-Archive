---
title: "[SOLVED] USB flash limit?"
date: 2008-09-12
forum: Hardware
---

### Post by worksofcraft on 2008-09-12
Just bought an 8Gb USB flash memory stick. Plug it in and it shows in the "Places" menu but clicking it I get: "Unable to mount location".
My old 256Mb memory stick works fine and this new one does work if I boot to Windows XP, btw that "XP" is not an emoticon - ;)

---

### Post by worksofcraft on 2008-09-16
Yo... did some googling and fixed it :-)
Just incase anyone else has this problem here is what to do:
WARNING this erases all data on the flash drive concerned!

1. Find out which is the USB flash dev:
- run df with no usb plugged in.
- plug in a known good USB flash and run it again...
spot the difference. For me it was /dev/hdc

2. Use sudo cfdisk -z /dev/hdc
- create partition using defaults then change type to 0C (fat32)

3 Plug into a Windows XP system, open mycomputer and click on the drive. It says it's not formatted, so format under windows.

Copy some random files from the Windows system, then plug it into your Ubuntu system and you can read the file and store some more!

---

