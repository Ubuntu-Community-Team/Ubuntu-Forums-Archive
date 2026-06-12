---
title: "Expand Raid"
date: 2008-09-11
forum: General Help
---

### Post by dgordon on 2008-09-11
Hi,

I'm trying to expand a RAID5 array that on an Adaptec 2410SA RAID card. It's currently a 3 drive array, and I've just added a fourth. 

The expansion went ok, but now when i try to take advantage of extra space by expanding the partition using gparted I get the following error:

"A partition cannot have a length of -1 sectors"

and it won't complete.

The size of the partition if it completed would be approx 1.5tb.

I can however create a partition for the unallocated space, but I would like to avoid this if possible.

Attached is a copy of the output from fdisk -l

```
Disk /dev/sda: 1500.2 GB, 1500216557568 bytes
255 heads, 63 sectors/track, 182390 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00058d95

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121593   976695741   83  Linux
/dev/sda2          121594      182390   488351902+  83  Linux

Disk /dev/sdb: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9640    77433268+  83  Linux
/dev/sdb2            9641        9733      747022+   5  Extended
/dev/sdb5            9641        9733      746991   82  Linux swap / Solaris

```

Any advice would be appreciated.

---

### Post by fjgaude on 2008-09-11
Gosh, I'm not sure if **gparted** can handle raid... is your card in raid5 mode, and do you have a driver for the card? is your raid5 software raid using **mdadm**?

What does **df -H** show?

---

### Post by dgordon on 2008-09-12
It's a hardware RAID using an Adaptec 2410SA, set as RAID5. The driver for it is apparently in the kernel.

The output of df -H

```
Filesystem             Size Used Avail Use% Mounted on
/dev/sdb1               79G   7.7G    68G  11% /
varrun                 131M   246k   131M   1% /var/run
varlock                131M      0   131M   0% /var/lock
udev                   131M    74k   131M   1% /dev
devshm                 131M    13k   131M   1% /dev/shm
lrm                    131M    41M    91M  32% /lib/modules/2.6.24-19-generic/volatile
/dev/sda2              497G   208M   471G   1% /media/disk
/dev/sda1              985G   742G   193G  80% /media/Media

```

I'm not really fussed on using gparted to expand the Raid, any method is fine.

---

### Post by fjgaude on 2008-09-12
I have no experience with what you are wanting to do... is there not a utility in the BIOS that permits expanding the array... or a program that came with the Adaptec to do the same.

I simply don't know of any tool to do what you wish. Seems to me if you add a drive to a hardware raid5 it should auto show the expanded space.

Question: the raid5 is mounted at /media/Media? and you are booting from /dev/sdb1?

---

### Post by dgordon on 2008-09-12
I've already expanded the array by using the Adaptec Storage Manager software. This doesn't expand the partition, it appears that it will need to be done at the OS level.

Like I said, I can set the extra space as a separate ext3 partition, I just cannot expand the current partition to take up the available space.

I'm not booting off it.

---

### Post by fjgaude on 2008-09-13
Well, my problem is I know no Linux partition editor that handles raid arrays. Most are based on **parted**, like **gparted**... and the **man** **pages** for it shows a command:

```
sudo parted resize partition start end
```

I've never used such... you will simply have to experiment with, learn how to use the command. But first, will it work on a raid array? I can't say!

Does anyone else know how to help here?

---

