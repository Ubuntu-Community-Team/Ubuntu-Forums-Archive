---
title: "iOne Scorpius P20 connectivity problem"
date: 2010-01-02
forum: Hardware
---

### Post by Jaykie on 2010-01-02
Hi all,

I'm using wireless keyboard/mouse combo called iOne Scorpius P20 and having some weird connectivity problems in Kubuntu 9.10 Karmic Koala. Keyboard works just fine when there is not too much CPU load e.g. under 20% but when it goes over the USB Receiver's led light stops blinking (as it does when receiving signal) and the keyboard/mouse stops responding. This can be easily repeated just by opening e.g. XBMC and the combo stops working. Also it seems to stop working when i load e.g. Youtube in firefox and start playing some videos. Any advice how to get it working properly? On the otherhand Logitech UltraX wired USB keyboard works just fine when extra load for CPU.
Could this be related to USB issue [https://bugs.launchpad.net/ubuntu/+bug/477843](https://bugs.launchpad.net/ubuntu/+bug/477843) ?

Motherboard is Asus P5QL Pro
 
jaykie@jaykie-desktop:~$ uname -r
2.6.31-16-generic

jaykie@jaykie-desktop:~$ lsusb
Bus 007 Device 003: ID 195d:7777 Itron Technology iONE Scorpius wireless keyboard
Bus 007 Device 002: ID 045e:0284 Microsoft Corp. Xbox DVD Playback Kit
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:c30e Logitech, Inc. UltraX Keyboard (Y-BL49)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Br,
Jaykie

---

### Post by Jaykie on 2010-01-08
Solved.

Keyboard started working just fine after removing Pulseaudio. It worked earlier with Pulseaudio but i upgraded to newer one and then the problem started.

---

