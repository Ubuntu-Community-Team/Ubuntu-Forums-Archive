---
title: "My Passport HD not showing up."
date: 2010-10-20
forum: Hardware
---

### Post by akumasaint on 2010-10-20
Hello, it's me again with another issue. :) 

I recently brought a 320gb WD Hardrive (My Passport) so I can put all my music,movies and such in there so I don't use up all the space in my laptop (Laptop is an older model Latitude from Dell, so not a lot of space...). The problem is that it's not showing up like it normally does when I pug in my flash drive (16gb Sandisk Micro) or when I plug in my mp3 player (Sana Fuze 4gb). I know it's plugged in because the light is on the bottom is coming on but that's it. 

I can tranfer my files from my flash drive to my hard drive from my computer (it still runs Windows XP...slowly) so I don't have to worry about getting files there but I just want to cut the middle man out and transfer them directly. Any ideas?

---

### Post by luvshines on 2010-10-20
What is the output of this command after you plug in HD:
```
sudo fdisk -l
```

If it lists your HD, something like, sdbX, probably towards the end, try mounting it manually:
```
sudo mkdir -p /media/myHD

## Replace X with number you see in fdisk output (if it is displayed)
sudo mount /dev/sdbX /media/myHD
```

---

### Post by akumasaint on 2010-10-20
> **luvshines said:**
> What is the output of this command after you plug in HD:
```
sudo fdisk -l
```

If it lists your HD, something like, sdbX, probably towards the end, try mounting it manually:
```
sudo mkdir -p /media/myHD

## Replace X with number you see in fdisk output (if it is displayed)
sudo mount /dev/sdbX /media/myHD
```

Okay I got it plugged in and this is what I got:

```
Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00009e5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3492    28046336   83  Linux
/dev/sda2            3492        3648     1253377    5  Extended
/dev/sda5            3492        3648     1253376   82  Linux swap / Solaris

```

I know it's not the first one because I tried that and got my laptop's hard drive...

---

### Post by akumasaint on 2010-10-20
Okay, I checked it with my flash drive and the hard drive. The flash drive shows up but not the hard drive.

---

