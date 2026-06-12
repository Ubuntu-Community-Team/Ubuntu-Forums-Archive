---
title: "GRUB 2 does not recogonize USB Keyboard during boot"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by mickcalcara on 2009-11-03
Ever since installing 9.10, I can not use USB keyboard during boot. I can not select installs from the boot menu unless a insert my old PS/2 keyboard. Anyone know of a fix for this?

---

### Post by oldfred on 2009-11-03
I think I had this problem with an update/install a year or so ago and my fix was in changing the BIOS settings. Ubuntu saw the mouse and keyboard but legacy grub would not until I changed the BIOS.

---

### Post by mickcalcara on 2009-11-03
Thanks for the reply. I checked my bios settings. I think everything is set correctly. It is interesting because my keyboard is fine in the bios but when Grub runs, I loose the USB  keyboard. When I installed Karmic a couple of days ago, I had to wait during the language screen to count down for the auto load with the Live CD; since I could not use my keyboard. Once booting starts, USB keyboard becomes active.

Somehow, it just gets disabled right at the beginning of the boot process.

---

### Post by Kyran_Be on 2009-11-04
Are you sure the settings in your BIOS are right?

I have 4 modes for legacy usb support on my BIOS:
auto
enabled
disabled
bios edit only

You should put it on enabled, both auto and bios edit only will most likely disable usb support after the bios has done his job. This means that your keyboard will only start to function after linux has loaded the usb modules and that leaves you without usb support in grub.

That said, the new grub2 should have optional usb support, but I can't get that to work on my machine (the usb support, grub2 is working just fine otherwise)

---

