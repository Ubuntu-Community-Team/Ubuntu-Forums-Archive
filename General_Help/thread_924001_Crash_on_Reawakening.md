---
title: "Crash on Reawakening"
date: 2008-09-19
forum: General Help
---

### Post by VengefulIce on 2008-09-19
Whenever i put the computer to sleep, hibernate or suspend, it always crashes.  I try to turn it on, i see a partial loading then the screen goes completely black and the monitor is sleeping.  Does anyone have a solution to this problem?

Thanks

---

### Post by anotherdisciple on 2008-09-19
I have had this problem occasionally. I don't know how to fix it, but I know that you are going to need to give more info if you want people to guide you better.

What are the specs on your computer?

CPU?
RAM?
SWAP?
Graphics Card?
Wireless Card?
etc...

That should help people help you.

---

### Post by tarps87 on 2008-09-19
Check your swap partition, it should be at least 1 1/2 times the size of your RAM for hibernating

---

### Post by VengefulIce on 2008-09-19
what is swap partition?

im running:
Pentium 4 2.8 Ghz
768mb ram
NVIDIA GeForce FX6150

---

### Post by tarps87 on 2008-09-22
Sorry for late reply.
Can you post the output of:```

sudo fdisk -l
```
(lower case L)
This will list all your partitions
It is where all the data in the ram will be stored when it hibernates and used if it runs out of memory. In Linux its a partition and in windows it a hidden file.

---

### Post by VengefulIce on 2008-09-22
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9444    75858898+  83  Linux
/dev/sda2            9445        9726     2265165    5  Extended
/dev/sda5            9445        9726     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x002b7ae9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24792   199141708+   7  HPFS/NTFS

---

### Post by tarps87 on 2008-09-23
It looks like you have a 2GB swap partition, how much ram do you have in your computer?

---

### Post by VengefulIce on 2008-09-23
i have 768 mb pc-3200

---

### Post by tarps87 on 2008-09-24
I doubt your swap partition is the problem then. I've just spotted the earlier post with the spec and the cpu should be fine, also I don't know of any problems with the graphics card.
Have you got a wireless card or tv cards?
What version of Ubuntu are you using?

---

### Post by VengefulIce on 2008-09-24
i'm just using ethernet..  no wireless or tv tuners

using Ubuntu Hardy Heron 8.04 LTS

---

