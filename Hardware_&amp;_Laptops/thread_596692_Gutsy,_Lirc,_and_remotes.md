---
title: "Gutsy, Lirc, and remotes"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by steelfanatic on 2007-10-29
Ok, I have two remotes (ATI remote wonder, Hauppage PVR-150) that will not work,what am I missing?  I installed Lirc and I thought I set them up properly.....here is dmesg | grep -i lirc :

[   31.119485] lirc_dev: IR Remote Control driver registered, at major 61
[   31.175740] lirc_atiusb: USB remote driver for LIRC $Revision: 1.61 $
[   31.175742] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[   31.177928] lirc_dev: lirc_register_plugin: sample_rate: 0
[   31.197932] lirc_atiusb[3]: X10 Wireless Technology Inc USB Receiver on usb4:3
[   31.209945] usbcore: registered new interface driver lirc_atiusb
[   36.606518] lirc_i2c: chip 0x10020 found @ 0x71 (Hauppauge PVR150)
[   36.606540] lirc_dev: lirc_register_plugin: sample_rate: 10

---

### Post by steelfanatic on 2007-10-30
Problem fixed here: [http://ubuntuforums.org/showthread.php?p=3658562](http://ubuntuforums.org/showthread.php?p=3658562) :)

---

