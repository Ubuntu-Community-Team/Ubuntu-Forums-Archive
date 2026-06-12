---
title: "Format A USB Dongle"
date: 2010-09-11
forum: Hardware
---

### Post by taamir on 2010-09-11
Hi, I am trying to format an old USB dongle to use as a disk on key.
when I plug it in to Ubuntu nothing happens, on XP it start an auto install program.
It doesn't show in GParted.

when I type lsusb I get:

```
Bus 005 Device 008: ID 0529:0001 Aladdin Knowledge Systems HASP v0.06

```

Any one know how I can format it ?

---

### Post by C.S.Cameron on 2010-09-11
Is it a hardware lock? Never heard of anyone reformatting one.

---

### Post by sikander3786 on 2010-09-11
Are you able to format it under Windows? Using the software that came with the USB?

---

### Post by taamir on 2010-09-11
I dont have the software that came with the USB if there is such a thing.
Windows XP doesn't recognize the USB device as removable disk - so I am unable to format it there.

---

### Post by coffeecat on 2010-09-11
> **taamir said:**
> It doesn't show in GParted.

when I type lsusb I get:

```
Bus 005 Device 008: ID 0529:0001 Aladdin Knowledge Systems HASP v0.06

```Any one know how I can format it ?

If Gparted is not seeing it then the system is probably not seeing the partitions, even though lsusb picks up the device. However, gparted sometimes does odd things, so it might be interesting to see if fdisk detects it. Plug the dongle in, and post the terminal output of:

```
sudo fdisk -l
```

---

### Post by taamir on 2010-09-11
Here it is:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c874a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29651   238168064   83  Linux
/dev/sda2           29651       30402     6028289    5  Extended
/dev/sda5           29651       30402     6028288   82  Linux swap / Solaris

```

Doesn't seems to find it...

---

### Post by howefield on 2010-09-11
> **taamir said:**
> on XP it start an auto install program.

Does it give you an icon on the Ubuntu desktop ?

---

### Post by taamir on 2010-09-11
On Ubuntu - No.
XP I can check it only tomorrow.

---

### Post by coffeecat on 2010-09-11
I've heard of the firmware in some USB external hard drives interfering with mounting, but not a USB dongle being entirely unrecognised by the system - and seemingly by XP too even though an executable autostarts. I'm sorry - I've no other ideas.

---

