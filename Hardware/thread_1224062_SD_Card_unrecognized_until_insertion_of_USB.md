---
title: "SD Card unrecognized until insertion of USB"
date: 2009-07-27
forum: Hardware
---

### Post by khamil8686 on 2009-07-27
I have an internal memory card reader which connects to one of four USB connectors on my motherboard. This card reader can read SD cards and has a USB slot, and it can read a bunch of other slots for cards ive never seen before :P But anyways. If i put in a SD card, ubuntu doesnt recognize it and pop up a screen with the disk's contents like it used to do (it worked in intrepid ibex) But once i put in a USB memory stick (only memory sticks, bluetooth stick didnt work) then the SD card contents window will pop up alongside a window with the contents of the USB memory stick directory, it doesnt matter if i use my case's usb ports or the port on the card reader, if i put in a USB stick then both windows and their contents will pop up. And then if i unmount and remove the USB stick and unmount and remove the SD card and put the SD card back in it will detect it and pop up a window just fine! it continues working fine until i reboot. even suspending and resuming doesnt bring this problem back, only rebooting does. ive tried also connecting the card reader to a different usb port(?) on my motherboard since my motherboard has 4 of them and still get the same problem with different ports. anyways any help would be appreciated :) this isnt a cant live without problem, i could buy a USB card reader for $10 and be fine, id just rather use this card reader instead of buying a different one. this card reader works fine in windows (dual boot) anyways, any help would be appreciated! im not sure where to look for an answer to this problem besides these forums :)

---

### Post by khamil8686 on 2009-07-27
Solved this with a workaround i posted in the link, seems usb-storage module doesnt get loaded on boot

[https://bugs.launchpad.net/linux/+bug/350739](https://bugs.launchpad.net/linux/+bug/350739)

---

