---
title: "ZTE ax226 dongle not responding"
date: 2012-09-03
forum: Hardware
---

### Post by Fikinator on 2012-09-03
Really sorry if this is in the worng forum but I dont know where else to go. Im a banglalion wimax user with their ZTE ax226 usb donge (says product ID: wixubb-116X238BD on the box) and been trying to get it to work on linux for some time (tried mint9 and 13 and pangolin which I'm on now) by following these insstructions [http://luv2know.wordpress.com/2012/05/28/3/](http://luv2know.wordpress.com/2012/05/28/3/) 

Think I accidentally put in a wrong p id on the device (with the beceem diagnostic tool) and now it wont even work in XP. The win connection manager cant find it and I get the generic dialog box for an unkown device, though it does say "usb device wixubb116X238Bd not installed" in XP.  The diagnostic tool cant find the device either so I'm stuck using my cellphone for internet now :( Really apreciate any help and orry again if this is the wrong place.

---

### Post by pdc on 2012-09-03
can you type 

> lsusb

in a terminal and copy and paste back here what you get

also copy this into a terminal

> dmesg | grep tty.............the | is actually shift-\

and tell us what you get

---

