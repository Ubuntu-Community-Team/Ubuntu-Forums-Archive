---
title: "ext3 partition sadly became unallocated after installing windows 7"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by kad78 on 2009-07-14
Any help would be much appreciated:
 
Origionally, I had Ubuntu(9.04) installed on an ext3 partition. I installed windows 7 from a bootable CD. However, after doing so, the ext3 partition became unallocated, and I have been unable to run Ubuntu or access my files on that partition. I have search on forums for days with no luck. I would love some help!!
 
Peace out.

---

### Post by merlinus on 2009-07-14
Can you run ubuntu from the live cd?  If so, open a terminal and post the results of:

```
sudo fdisk -l
```

---

### Post by Sef on 2009-07-14
Did you install Windows after Ubuntu?   If so, then you have overwritten GRUB, and it needs to be reinstalled.   User [Super GRUB Disk]("http://supergrubdisk.org") to restore it.

---

### Post by kad78 on 2009-07-14
> **Sef said:**
> Did you install Windows after Ubuntu? If so, then you have overwritten GRUB, and it needs to be reinstalled. User [Super GRUB Disk]("http://supergrubdisk.org") to restore it.
 
Thanks for you attention.
 
Yes I did install Windows after Ubuntu. However, I was aware of GRUB being wiped by the windows boot loader, so I tried to reinstall it using easyBCD. However, the partition was not recognised, and thus it would not work. Therefore, regardless of whether GRUB is installed [i think] there is another problem to be solved concerning the ext3 partition.
 
I shall obtain a live cd and post the results of: sudo fdisk -l in a few hours.

---

### Post by csabo2 on 2009-07-14
I would say download gparted bootable CD (gparted.sourceforge.net) and boot it up, windows may have just used the whole drive :(

---

### Post by coffeecat on 2009-07-14
> **csabo2 said:**
> I would say download gparted bootable CD (gparted.sourceforge.net)

The OP has said that they are going to get the Ubutu live CD to run fdisk. The live CD includes Gparted. Why would the OP need to download the gparted CD as well?

---

### Post by kad78 on 2009-07-15
The results of           sudo fdisk -l

```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1318       15595   114688035    b  W95 FAT32
/dev/sda2   *       15596       29423   111073280    7  HPFS/NTFS
/dev/sda3           29424       38914    76229546+   f  W95 Ext'd (LBA)
/dev/sda5           38587       38914     2620416   dd  Unknown

```sda5 is the partition containing 'Media Direct'. sda3 is an extended partion containing 70GiB of unallocated space (where ubuntu is hiding) and media direct is contained. sda1 is just used for storage. sda2 contains windows 7.

---

### Post by kad78 on 2009-07-19
I managed to retrieve my data and I then reinstalled ubuntu. As with windows installed first this time the process was easier; so i have no problem now.

---

### Post by mandicoot on 2009-08-09
Hi all,

I had the same problem - I had an extended partition which contained ~ and /
(home and boot partitions)

I installed Windows 7, assuming that though I would injure grub it wouldn't be fatal - I would easily be able to repair it. 

Alas, I had been overconfident, and like the OP I have ended up with an extended partition that is listed in gparted as "unallocated". I'm fairly resigned to reinstalling, first Win7 and then Ubuntu, but first I'd like to be able to get my data out of the stealthed ubuntu in the extended partition. I see that the OP managed to get his data back, can anybody tell me how to do this please?

---

### Post by stlsaint on 2009-08-09
EASYBCD is used for vista not for GRUB!!

---

### Post by merlinus on 2009-08-09
You might try testdisk to recover the partition.

---

### Post by jhahoneyk on 2010-02-10
Happened to me too. Damn whoever wrote the windows setup. First they delete GRUB, and now they corrupt ext filesystem.

---

### Post by kad78 on 2010-06-22
I stumbled across this thread again and realised that I forgot to post back. I did indeed use testDisk to recover the partition, and then I reinstalled ubuntu again. TestDisk works very well thank you.

---

### Post by bruno9779 on 2010-06-22
The same happened to me some months ago when I tried to install win7

Win7 uses 2 primary partitions, and disregards your previous setup for the choice of the second one.

The problem I run into was actually worse, as I already had 3 primary partitions, and win7 tried to create a total of 5 (legacy limit is 4)

Testdisk saved most of my data, and I haven't felt like trying to install win7 again. Such a bad and painful first experience with it has completely put me off.

So, that complementary (my work) Win7 Ultimate disk has found a new home in the rubbish bin

---

