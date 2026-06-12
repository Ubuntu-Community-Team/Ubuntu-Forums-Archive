---
title: "Need to format an SD card with failed ubuntu install"
date: 2009-06-30
forum: Hardware
---

### Post by wordrush on 2009-06-30
Hi everyone.

Long story time warning :P

I got myself in a bind.  I was having issues with my install on my Dell mini 9 laptop (Dell provided ubuntu, but I screwed it up) so I decided to do a fresh install.

During the process of installing ubuntu on my hard drive I also decided I would like it on my 16 GB Transcend SD card as well.  I went through the entire install process only to get to the end and a fatal error occured.  I can't remember exactly what the error was right now though if it is necessary info I can go reproduce the error.

Well since then I have decided I don't want ubuntu installed on that card (I really just want to install programs to it, different thread :p).  Problem is I can't figure out how to format it.  I have used gparted, but it can not find the drive.  I tried booting onto it and then using gparted, but it is not bootable.  I tried fdisk, but that didn't work either.

I am somewhat of an amatuer when it comes to linux op's.  I think I know just enough to get myself in trouble.  That being said, fdisk or gparted may still work, I just haven't thought of the fix.

In any case, does anybody know how I can format this sd card?

The card fails to mount properly but it does show up under my /dev directory as three separate drives.

The relevant output from sudo fdisk -l

```
Disk /dev/mmcblk0: 16.0 GB, 16070475776 bytes
255 heads, 63 sectors/track, 1953 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ef631df

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        1866    14988613+  83  Linux
/dev/mmcblk0p2            1867        1953      698827+   5  Extended
/dev/mmcblk0p5            1867        1953      698796   82  Linux swap / Solaris
``` I will happily answer any questions :p.


[SIZE="4"]
Edit:  I may have figured this one out by doing gparted /dev/mmcblk0/[/SIZE]

---

### Post by 73ckn797 on 2009-06-30
Could you boot the live CD and run Gparted from Their? I assume you did try that.

---

### Post by lindsay7 on 2009-06-30
You should be able to do it with Gparted. Unmount the card and format it as you choose, fat32, ntsf, ext3, ......

---

### Post by wordrush on 2009-06-30
Ok, haha, I figured it out.  I gparted the dev/ directory, then once I got the Linux, and Linux swap off of there I was able to use fdisk to format the entire disk so it wasn't in multiple partitions.

Thanks so much for the advice.

---

