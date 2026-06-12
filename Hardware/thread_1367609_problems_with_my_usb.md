---
title: "problems with my usb"
date: 2009-12-29
forum: Hardware
---

### Post by coyotemk on 2009-12-29
Hello
i have a USB flash drive**,** and i have a problem with it. When i put it on i cant see it in /media/. But i've installed Gnome Format, and he reads it, but when i try to format it i get the message: 
Error mounting: mount exited with exit code 32: mount: /dev/sdb1: can't read superblock

I've tryed to understand, but i didnt find anything, only when i type "lsusb" in a terminal, he can see it.
Anyone has an idea??
P.S. i'm using ubutnu 9.10

---

### Post by taurus on 2009-12-29
If you want to format a drive, you cannot mount it.  It has to be unmounted first before you can format it.  Try installing gparted (System -> Administration -> Software Sources) and see if that would let you reformat your thumbdrive.

---

### Post by coyotemk on 2010-01-02
i've tried GParted also. When he's reading all the partition it takes a lot of time if i put the usb. After that it tell's me that the memory of my usb is unallocated, and when i start to format it, i have messages in my terminal like this:
  /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/host3/target3:0:0/3:0:0:0 (4197)
  /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/host3/target3:0:0/3:0:0:0/block/sdb (4198)
  /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/host3/target3:0:0/3:0:0:0/block/sdb (4199)
  /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/host3/target3:0:0/3:0:0:0 (4200)
  /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/host3/target3:0:0/3:0:0:0/block/sdb/sdb1 (4201)
  /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/host3/target3:0:0/3:0:0:0/block/sdb (4202)
  /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/host3/target3:0:0/3:0:0:0

Is this means that my usb is damaged or something :confused:?

---

