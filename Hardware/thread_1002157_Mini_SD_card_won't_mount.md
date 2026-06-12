---
title: "Mini SD card won't mount"
date: 2008-12-04
forum: Hardware
---

### Post by afilonov on 2008-12-04
I have system76 laptop (Gazelle Performance Black) with an SD card reader. It worked for all SD cards I have. But today I tried mini SD card using SD adapter. System recognizes the card but doesn't mount it. I can mount it manually, but I'm not sure it's a safe method. Here's corresponding piece from /var/log/syslog:

Dec  4 15:00:14 gazelle kernel: [ 2098.655887] mmc0: new SD card at address 0001
Dec  4 15:00:14 gazelle kernel: [ 2098.656047] mmcblk0: mmc0:0001 SD 1994240KiB 
Dec  4 15:00:14 gazelle kernel: [ 2098.656099]  mmcblk0: p1


If I use normal SD card, it's mounted automatically, and log looks like this:

Dec  4 14:58:30 gazelle kernel: [ 1995.190753] mmc0: new SD card at address b368
Dec  4 14:58:30 gazelle kernel: [ 1995.191033] mmcblk0: mmc0:b368 SD    975360KiB 
Dec  4 14:58:30 gazelle kernel: [ 1995.191090]  mmcblk0: p1
Dec  4 14:58:30 gazelle hald: mounted /dev/mmcblk0p1 on behalf of uid 1000

OS is Ubuntu Hardy (8.04) with all latest updates.

Any ideas?

---

### Post by taurus on 2008-12-04
Yes, it is safe to mount manually from a terminal.  Just remember to unmount it first before you unplug it.

---

### Post by Jose Catre-Vandis on 2008-12-04
I have had similar problems with micro sd cards just not being recognised, formattable or working, using the SD piggy back adapter (that usually comes with the micro sd card). I got hold of a usb adapter for micro sd cards and that solved all my issues.

---

### Post by afilonov on 2011-06-02
Upgrade to 10.04 solved this issue.

---

