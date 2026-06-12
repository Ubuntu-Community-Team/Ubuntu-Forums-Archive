---
title: "Unable to install on eee PC 4G"
date: 2010-01-09
forum: Hardware
---

### Post by gewitty on 2010-01-09
I've been trying to install 9.10 Remix on my eee pc 4G. It runs Most other netbook distros OK, but I can't get 9.10 to load. I've tried creating a USB install stick using both USB Startup Disk Creator and also Unetbootin, but the result is the same: When I run the installation process, I get as far the language choice screen, then the Ubuntu logo appears. After that, the system hangs for several minutes until I get a series of error messages as follows:

stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0
stdin: error 0

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for list of commands.

(initramfs) /init: line 1: can't open udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/1d.2/usb3/3-1:1.0/host3/target3:0:0/3:0:0:0/block/sdc/sdc1 (1091) /dev/loop0: no such file
mount: mounting udevadm settle - timeout os 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/host3/target3:0:0/3:0:0:0/block/sdc/sdc1 (1091) /dev/loop0 on //filesystem.squashfs failed: No such device
Can not mount udevadm settle - timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1:1.0/host3/target3:0:0/3:0:0:0/block/sdc/sdc1 (1091) /dev/loop0 (cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

I also tried the same memory stick on a different Netbook (an HP Mini) and it worked OK.

Any ideas on what the problem might be?

---

### Post by gewitty on 2010-01-09
Not sure why this resolved things, but I had a 4Gb SD card installed on the eee. I tried removing this before repeating the installation and everything worked!

---

### Post by Alex!!!! on 2010-01-09
Well, if you have other distros running well... What do you mean 'other distros'? Ubuntu Hardy, Edgy? Than you shouldn't install Karmic, as it is pretty new and may have some errors. But I am running it and it feels quite good. Try downloading a fresh copy of it. Maybe you downloaded it wrong,  or didn't burn the disc right?

---

### Post by kierano on 2010-09-14
Same problem, also eee PC 4G. I had an old copy of eeebuntu installed, and wanted to completely wipe it (it had some weird disk problem that was stopping things like apt and svn from working).

And I also had an SD card inserted. After ejecting SD card and rebooting, it worked fine. Really weird.

---

