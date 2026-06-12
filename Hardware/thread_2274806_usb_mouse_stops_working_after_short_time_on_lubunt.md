---
title: "usb mouse stops working after short time on lubuntu 14.04"
date: 2015-04-22
forum: Hardware
---

### Post by saxman25 on 2015-04-22
hallo,

i have lubuntu 14.04 / lxde on a desktop pc (AMD64x2, nvidia GT440 via 331.113 driver)

after a unspecified amount of time (several minutes up to several hours) my usb mouse stops working. no movement, no button click possible.

choosing a different usb port at this time does nothing - no recognition of plugging in a mouse (verified via dmesg)

so as a workaround i attached a second mouse from the beginning. both are recognized during bootup and work. so when the first mouse stops i use the second one. until it also goes dead. this may have doubled the time between reboots, but this is no real solution for me.

there seems to be no preference as to which mouse stops working first (both different brands/models).

Does anyone has a suggestion as to what may be wrong or how to check from where the bug originates?

thanks

---

### Post by dino99 on 2015-04-22
Sometimes i have that issue too; but its often due to the mouse batteries i need to move. Is yours having batteries too ?
Or 14.04 lubuntu possibly have an issue dealing with usb; or the bios settings are badly set about usb (check it) 

but first, from a terminal, run these commands one by one:
sudo update-pciids
sudo update-usbids

---

### Post by saxman25 on 2015-04-22
no batteries - they both are usb cable mice

tried the two update commands and will see if it does anything

---

### Post by saxman25 on 2015-04-23
UPDATE: after ~1day the mouse still seems to work. so the solution worked! (it never lasted this long without freezing)

what  i don't understand - shouldn't those id-lists being updated with the normal  system updates? 
and if not - how old are the id-lists shipped with  14.04? my mice are at least 5 years old, so they ought to be even in old lists....

---

### Post by dino99 on 2015-04-23
sadly they are not checked so often, and mainly stay as is after installation/dist-upgrading. It get updated only with the devices database, which happen 1 or 2 times for a given release.

in case a device is unknow (rare or too new) then a request can be sent to [https://pci-ids.ucw.cz/](https://pci-ids.ucw.cz/)
[https://wiki.debian.org/HowToIdentifyADevice/PCI](https://wiki.debian.org/HowToIdentifyADevice/PCI)

---

