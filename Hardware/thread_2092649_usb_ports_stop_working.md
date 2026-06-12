---
title: "usb ports stop working"
date: 2012-12-08
forum: Hardware
---

### Post by suprkain on 2012-12-08
I have read various post all over the internet that I can find and I can't seem to fix my issue.  What happens is the usb ports on the back of my computer stop working all together however the usb ports on the front of my computer still work.  Can someone please help me.  I have a dell xps 8100 and I'm running 12.04. I have done several fresh installs but nothing works.  This is the last thing keeping my from switching from Windows to Ubuntu permanently.

---

### Post by suprkain on 2012-12-10
anybody?

---

### Post by crysman on 2012-12-10
> **suprkain said:**
> I have read various post all over the internet that I can find and I can't seem to fix my issue.  What happens is the usb ports on the back of my computer stop working all together however the usb ports on the front of my computer still work.  Can someone please help me.  I have a dell xps 8100 and I'm running 12.04. I have done several fresh installs but nothing works.  This is the last thing keeping my from switching from Windows to Ubuntu permanently.

Well, on my ASUS U36S running Xubuntu 12.10 there is similar problem. Whenever I suspend the laptop, the right USB port (which is USB 3) is not working any more after suspend. Two USB ports on the left side are going on working, though... It is very annoying! I've still not figured out how to fix it. I am not using any special boot options:
```
$ cat /proc/cmdline 
BOOT_IMAGE=/vmlinuz-3.5.0-19-generic root=UUID=d7ba62fe-cc44-4f1d-bade-16512306f8f0 ro
```

lsusb gives (currently USB 3 not working after suspend):
```
$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 054: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 004: ID 04f2:b1b9 Chicony Electronics Co., Ltd Asus Integrated Webcam
Bus 001 Device 005: ID 08ff:1680 AuthenTec, Inc. AES1660 Fingerprint Sensor
```

I am quite unhappy about this, too :(
#crysman

---

### Post by suprkain on 2012-12-12
hello?

---

### Post by crysman on 2012-12-13
> **suprkain said:**
> hello?

Hombre, take it easy, nobody is obliged to answer you, this is not a support line to commercial product... Have patience and try to keep looking for the answer. If you find out something, leave a post here also.
#crysman

---

