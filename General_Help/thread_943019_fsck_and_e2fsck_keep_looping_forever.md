---
title: "fsck and e2fsck keep looping forever"
date: 2008-10-09
forum: General Help
---

### Post by Cyber Akuma on 2008-10-09
EDIT: I should probably mention this in case it applies:

A few days before this started happening, I had resized my Ubuntu partition, however, after the resize Ubuntu worked fine. It was only a few reboots and days later that the partition corrupted, so I don't think this is directly the cause of the problem.

Ok, my Linux partition suddenly got corrupted recently, at first only Linux would not boot so it wasn't much of a big deal, but then grub started to fail at stage 2, I am pretty sure my config files for grub are on my linux partition.

So I tried to boot with a livecd to repair the damage, but when I run fsck or e2fsck it just keeps displaying the same errors then starting over forever in an infinite loop.

Any advice? I have several oses so if possible I would like to recover my menu.lst config file for grub.

---

### Post by k2chris1983 on 2008-10-09
Your Conf file for grub should be in /boot/ but if your partition is corrupted, you may have bigger problems like: Bad Sectors, Corrupted Partition and so on. 

I think you should do a Hard Drive test and see if your hard drive is dying...

---

### Post by Tanker Bob on 2008-10-09
Try downloading and using [Super Grub Disk](http://www.supergrubdisk.org/) to boot the partition, then make your fixes.

---

### Post by Cyber Akuma on 2008-10-10
> **k2chris1983 said:**
> Your Conf file for grub should be in /boot/ but if your partition is corrupted, you may have bigger problems like: Bad Sectors, Corrupted Partition and so on. 

I think you should do a Hard Drive test and see if your hard drive is dying...

The other 5 or so partitions on this disk are all are mountable and readable, plus I did a surface scan on the Linux exf3 partition and it didn't find any problems.

I am not sure WHERE /boot is physically located on my harddrive, but I am pretty sure it is not located in it's own partition because I don't see it in any disk manager I use, I assume it is in the exf3 partition.

My partitions are setup like this:
Primary - Toshiba System Partiton - NTFS - 1GB
Primary - Vista Partiton - NTFS - about 120GB
Primary - MacosX Partition - HFS+ - about 15GB
Extended:
----Logical - Ubuntu partition - exf3 - about 10 to 15 gigs
----Logical - Storage - FAT32 - About 55 gigs (I designed this partition so all the oses on the system would be able to read-write from it easily)
----Logical - Linux Swap - Linux Swap - about 1 to 1.5 gigs.

Those first two partitions came with the system, I then installed Ubuntu and then macosx.

---

### Post by Cyber Akuma on 2008-10-11
Anybody?

---

### Post by Tanker Bob on 2008-10-11
> **Cyber Akuma said:**
> Anybody?
Did you try Super Grub Disk as I suggested? I didn't see you mention it.

The other thing that comes to mind is that you have the Linux root partition in an extended partition. I don't know if it's a hard and fast rule, but I believe that it should be a primary partition, as should the home directory and swap partition. I've tried it before and have found that Linux doesn't care much for extended partitions. It will read them fine, but the mounting tends to be squirrely.

Also, GRUB is easily confused by a large number of drives and/or partitions. It doesn't always get their loading order correct. Working with Super Grub Disk can help, followed my manually fixing menu.lst with what you learn.

---

### Post by geirha on 2008-10-11
First of all, I'd recommend you backup the partition in the current state. If there's a problem with the disk, more and more data may be lost the more you try to fix it, so on the live cd, install ddrescue, mount your big NTFS drive, or preferably an external drive with NTFS or ext3 on it, and run ```
dd_rescue /dev/sda5 /media/disk/sda5.image
``` Assuming /dev/sda5 is the ext3 partition and an non-FAT partition with enough space is mounted at /media/disk/. (FAT32 have a maximum filesize of 4GB, so it won't hold the entire partition)

Read about ddrescue at [http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html](http://www.debianadmin.com/recover-data-from-a-dead-hard-drive-using-ddrescue.html)

After that, could you post the output you get when you run fsck on that partition?

---

### Post by Cyber Akuma on 2008-10-11
EDIT:

Sorry about this, I forgot to mention the resize, I posted about that just now in my original post.

> **Tanker Bob said:**
> Did you try Super Grub Disk as I suggested? I didn't see you mention it.

Not yet, I am reading up on it.

But won't this just give me an alternate way of starting the bootloader?

I tried loading Linux off a LiveCD, and the ext3 partition is unmountable, so I doubt I will be able to use Super Grub to load the menu.lst from my exf3 partition.

> **Tanker Bob said:**
> The other thing that comes to mind is that you have the Linux root partition in an extended partition. I don't know if it's a hard and fast rule, but I believe that it should be a primary partition, as should the home directory and swap partition. I've tried it before and have found that Linux doesn't care much for extended partitions. It will read them fine, but the mounting tends to be squirrely.

Well, I didn't really have a choice. I tried and I couldent get the laptop to boot without the Toshiba System Partition (I don't have a Vista install disk to start over), and out of Vista, MACOSX, and Linux, I figured Linux would give me the least trouble booting off an extended partition.[/QUOTE]

> **Tanker Bob said:**
> Also, GRUB is easily confused by a large number of drives and/or partitions. It doesn't always get their loading order correct. Working with Super Grub Disk can help, followed my manually fixing menu.lst with what you learn.

Its been working fine for nearly a year now. Grub itself didn't fail, it can't load its stage 2 files because the linux partition they are stored on failed.

---

### Post by geirha on 2008-10-11
> **Cyber Akuma said:**
> EDIT:

Sorry about this, I forgot to mention the resize, I posted about that just now in my original post.

Sounds like a resize gone bad then. What's the output of ```
sudo fdisk -l
```

> **Tanker Bob said:**
> 
The other thing that comes to mind is that you have the Linux root partition in an extended partition. I don't know if it's a hard and fast rule, but I believe that it should be a primary partition, as should the home directory and swap partition. I've tried it before and have found that Linux doesn't care much for extended partitions. It will read them fine, but the mounting tends to be squirrely.


No, linux will work just as well off a primary partition as a logical partition, it really doesn't mind. Windows however, is a completely different story.

---

### Post by Cyber Akuma on 2008-10-11
> **geirha said:**
> What's the output of ```
sudo fdisk -l
```

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x024a7aed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1542208+   6  FAT16
/dev/sda2   *         193       19380   154125236    7  HPFS/NTFS
/dev/sda3           19380       21358    15890647+  af  Unknown
/dev/sda4           21359       30401    72637897+   f  W95 Ext'd (LBA)
/dev/sda5           21359       22743    11124981   83  Linux
/dev/sda6           22744       30210    59978646    b  W95 FAT32
/dev/sda7           30211       30401     1534176   82  Linux swap / Solaris

```

---

### Post by Cyber Akuma on 2008-10-15
Umm, does that output help?

---

### Post by geirha on 2008-10-15
Well, the partition table looks quite ok, so I think the most useful data would be the actual output of fsck.

---

### Post by Cyber Akuma on 2008-10-19
Sorry for not responding for a while.

Well, I just bit the bullet and formatted the partition.

I coulden't figure out how to reinstall just GRUB stage 2 on it off the ubuntu 7.10 livedisk so I just reinstalled 7.10 and plan to reformat it to install 8.10 fresh when its out of beta.

---

