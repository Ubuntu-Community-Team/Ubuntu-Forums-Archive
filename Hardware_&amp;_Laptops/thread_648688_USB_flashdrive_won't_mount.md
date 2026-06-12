---
title: "USB flashdrive won't mount"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by bakaeigo on 2007-12-23
When I plug in my flash drive, Gutsy doesn't recognize it. The light on it flashes for an instant, but nothing else happens. This seems to be the case with any USB devices that aren't connected on startup. Anyone know how to fix this?

EDIT: I dual-boot with Windows XP, which works fine.

---

### Post by Dngrsone on 2007-12-23
Have you tried mounting it, manually?

---

### Post by eggdeng on 2007-12-24
To mount manually, plug in the device and run ```
dmesg | tail
```
This will tell you how the device and its partitions are recognised. Then follow the steps at [http://ubuntuforums.org/showthread.php?t=405384]("http://ubuntuforums.org/showthread.php?t=405384") post #3.

---

### Post by orange__boy on 2007-12-24
Reboot into windows XP and plug in the USB device and then dismount it correctly in WIndows. You may find that this fixes your problems with USB in Ubuntu.

rgds

---

### Post by bakaeigo on 2007-12-24
My "dmesg | tail" came out like this:
> [  287.673651] hub 5-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[  290.547048] hub 5-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[  298.403940] hub 5-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[  303.475349] hub 5-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[  305.801216] hub 5-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[  310.716694] hub 5-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[  340.137657] hub 5-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[  370.417838] hub 5-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[  439.274632] hub 5-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[ 1632.337711] usb 5-5: USB disconnect, address 6

This doesn't look very similar to the one in the thread you showed me, will the steps still work?

---

### Post by bakaeigo on 2007-12-24
I tried the steps in that link, but the terminal said that "dev/sbd1" didn't exist.

---

