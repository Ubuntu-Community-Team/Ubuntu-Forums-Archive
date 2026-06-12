---
title: "Partition issues"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by snowboardb86 on 2009-05-28
I have installed Ubuntu 9.04 to dual boot on my laptop with Vista. I used Paragon Partition manager to create a 50 GB partition that I planned on installing Ubuntu on. However I apparently selected the wrong option and installed it side-by-side to Vista on my 250GB partition. Is there anyway that I can 'move' my install to the other partition, or just have linux mount it and use it as the main file system? 

P.Ss. I have looked to merge the partitions but Paragon cannot do it. It shows as an Extended Partition.

Thanks in advance for you help!

---

### Post by raymondh on 2009-05-28
> **snowboardb86 said:**
> I have installed Ubuntu 9.04 to dual boot on my laptop with Vista. I used Paragon Partition manager to create a 50 GB partition that I planned on installing Ubuntu on. However I apparently selected the wrong option and installed it side-by-side to Vista on my 250GB partition. Is there anyway that I can 'move' my install to the other partition, or just have linux mount it and use it as the main file system? 

P.Ss. I have looked to merge the partitions but Paragon cannot do it. It shows as an Extended Partition.

Thanks in advance for you help!

Hi,

Wish I could see what your hard drive looks like.  It would help if you could/would provide either an output of gparted or fdisk -l

For gparted, using ubuntu, go to system > administration > partition editor to bring up gparted.  Take a screenshot and post it back.

For an fdisk output, go to a terminal (accessories > terminal) and type

```
sudo fdisk -l
```

that's a small L.  Post back its' output as well.

edit : thanks merlinus

Thanks :)

---

### Post by merlinus on 2009-05-28
I do believe you need to run

```

sudo fdisk -l

```

---

### Post by snowboardb86 on 2009-05-28
Here is the fdisk output, however I do not have partition editor when I go to system > administration.

stumper@stumper-laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x676195ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2   *        1306       31985   246431931+   7  HPFS/NTFS
/dev/sda3           31986       32311     2618595    5  Extended
/dev/sda4           32312       38913    53030565    7  HPFS/NTFS
/dev/sda5           31986       32289     2441848+  83  Linux
/dev/sda6           32290       32311      176683+  82  Linux swap / Solaris


> **raymondhenson said:**
> Hi,

Wish I could see what your hard drive looks like.  It would help if you could/would provide either an output of gparted or fdisk -l

For gparted, using ubuntu, go to system > administration > partition editor to bring up gparted.  Take a screenshot and post it back.

For an fdisk output, go to a terminal (accessories > terminal) and type

```
sudo fdisk -l
```that's a small L.  Post back its' output as well.

edit : thanks merlinus

Thanks :)

---

### Post by merlinus on 2009-05-28
Looks like you have an OEM recovery partition in sda1, and two windows (ntfs) partitions, sda2 and sda4, and then linux in sda5.

So are you wanting to combine the two windows partitions, or remove the second and grow the linux one into it?

sda2 seems to be vista.

---

### Post by snowboardb86 on 2009-05-28
I attached a screenshot of what the partition manager shows. What I want to do is take the extended partition (which is where Linux is) and put it on the D: partition, which I created for Linux in the first place. I can clean up the partitions and just format it, then re-install Ubuntu again. My question with that would be when do I specify what partition I want it installed on in the install process. When I got to that part of the install I don't recall where I could tell it that I wanted it on the D: partiton seperate from Windows.

Thanks again!!

> **merlinus said:**
> Looks like you have an OEM recovery partition in sda1, and two windows (ntfs) partitions, sda2 and sda4, and then linux in sda5.

So are you wanting to combine the two windows partitions, or remove the second and grow the linux one into it?

sda2 seems to be vista.

---

### Post by merlinus on 2009-05-28
You can reinstall and select manual at the partitioner, and tell it to use all of sda4.  It will create a swap partition as well.

At the moment linux is only some 2+G, and the 50G is formatted as ntfs, not ext3.

---

### Post by Bartender on 2009-05-28
If you boot from a LiveCD, and go to "Run Ubuntu without making any changes", you'll find GParted in System>ADministration.  It's pretty easy to save a screenshot.  Plug in a thumbdrive, wait for it to show up on the desktop, then go into GParted, take the screenshot, save it to Desktop, drag/drop to thumbdrive.

---

