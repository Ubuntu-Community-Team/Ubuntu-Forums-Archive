---
title: "Jetway Mini-Top Remote almost working in 11.04"
date: 2011-10-10
forum: Hardware
---

### Post by kireol on 2011-10-10
I have a Jetway Mini-Top HBJC600C99-352W-BW and need help with 1 last part.  

In XBMC the remote works ALMOST perfectly except for "up, down, left, right, and select".  Everything else works, pause, play, the mouse, volume, etc.  This is out of the box.  I did not install lirc or anything.

The jetway comes with a built in IR + remote that is an Aureal HID.  I think ubuntu sees it as a secondary mouse and a secondary keyboard instead of a remote.  But I'm kind of new to remotes so i'm only guessing on this part.

I'm running 32 bit 11.04.  Also running Darma XBMC.

dmesg shows
```
   16.657597] input: Cy se&#810;www.ir www.irfmedia.com UIR as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4.1/1-4.1:1.0/input/input6
[   16.658312] generic-usb 0003:0755:2626.0001: input,hidraw0: USB HID v1.10 Keyboard [Cy se&#810;www.ir www.irfmedia.com UIR] on usb-0000:00:1d.7-4.1/input0
[   16.663813] input: Cy se&#810;www.ir www.irfmedia.com UIR as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4.1/1-4.1:1.1/input/input7
[   16.664356] generic-usb 0003:0755:2626.0002: input,hidraw1: USB HID v1.10 Mouse [Cy se&#810;www.ir www.irfmedia.com UIR] on usb-0000:00:1d.7-4.1/input1

```


and lsusb

```
lsusb
Bus 005 Device 002: ID 0d8c:013c C-Media Electronics, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c529 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0755:2626 Aureal Semiconductor 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


How can I get the final 5 buttons to work?  Up, down, left, right and select.

Thanks!

---

