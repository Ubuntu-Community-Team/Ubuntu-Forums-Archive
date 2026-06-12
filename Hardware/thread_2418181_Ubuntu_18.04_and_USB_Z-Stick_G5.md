---
title: "Ubuntu 18.04 and USB Z-Stick G5"
date: 2019-05-03
forum: Hardware
---

### Post by erics-bad-habit on 2019-05-03
I just did a fresh install of Ubuntu 18.04 for a home automation server but my Ubuntu user doesn&#8217;t see  the Z-Stick G5. Z-stick shows up in dmesg but not in lsusb or ls  /dev/ttyACM*. Any clues? Thanks. nnn@arm:~$ sudo dmesg
[sudo] password for nnn:
&#8230;
[  673.996244] usb 1-1: new full-speed USB device number 3 using musb-hdrc
[  674.145221] usb 1-1: New USB device found, idVendor=0658, idProduct=0200
[  674.145242] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[  674.152807] cdc_acm 1-1:1.0: ttyACM0: USB ACM device
nnn@arm:~$ sudo lsusb
Bus 001 Device 003: ID 0658:0200 Sigma Designs, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
nnn@arm:~$ sudo ls /dev/ttyACM*
/dev/ttyACM0

---

