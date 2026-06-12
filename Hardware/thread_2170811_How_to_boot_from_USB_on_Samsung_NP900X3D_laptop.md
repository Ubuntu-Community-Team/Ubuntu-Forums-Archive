---
title: "How to boot from USB on Samsung NP900X3D laptop"
date: 2013-08-27
forum: Hardware
---

### Post by throaway on 2013-08-27
Please let this thread stay. After five hours of trying I'd like to share my findings with everyone.

Samsung Series 9 notebook
Samsung NP900X3D

Problem: Couldn't start from USB Stick.

some of these points are probably not necessary, but it worked this way for me:

update bios firmware on windows (if you want to get rid of windows afterwards)

format an usb stick by creating ms-dos partition table (e. g. with gparted)

format the usb stick with fat32 (e. g. with gparted)

remove usb stick and put it back in

use unetbootin (imagewriter etc. will probably also work. haven't testet it) to flash ubuntu (used 13.04 amd64) to flash the usb stick with your iso (takes several minutes)

deactivate "fast bios mode" in bios (press f2 on boot to get into the bios)

change boot order in bios, maybe disable hdd boot with pressing shift + 1 in the boot order bios menu

start from usb stick (by the way, with f10 you can get a list of devices to choose to boot from)


hint: if your usb stick doesn't appear in the list of devices to boot from try another usb stick.

---

