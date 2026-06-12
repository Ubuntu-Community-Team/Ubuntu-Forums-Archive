---
title: "[SOLVED] Need help reinstalling ubuntu"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by hibajugalala on 2009-01-10
I'm dual booting Windows Vista and ubuntu.
I screwed up my ubuntu a while ago and i need to reinstall it.
I don't want to screw up my windows vista and I do not have a windows vista disc.

---

### Post by taurus on 2009-01-10
Boot from the LiveCD.  When you get to the partition screen, pick Manual and tell the installer to mount the old Ubuntu partition to / and format it.  Again, make sure you mount the right partition to / or the installer will complain about no root filesystem.  You don't have to do anything with the swap partition since the installer knows how to handle that.

---

### Post by hibajugalala on 2009-01-10
How do i check what partition my ubuntu is on?

---

### Post by taurus on 2009-01-10
What's the output of this command from a terminal from the LiveCD?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by chex_m8 on 2009-01-10
you can use the live cd and go into Gparted or open terminal and type sudo fdisk -l.

---

### Post by hibajugalala on 2009-01-10
the output is:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26e271ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1529    12281661   27  Unknown
/dev/sda2   *        1530       15979   116068352    6  FAT16
/dev/sda3           15979       16810     6668160    7  HPFS/NTFS
/dev/sda4           16811       30401   109169707+   5  Extended
/dev/sda5           16811       29843   104687541   83  Linux
/dev/sda6           29844       30401     4482103+  82  Linux swap / Solaris

---

### Post by taurus on 2009-01-10
> **hibajugalala said:**
> the output is:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26e271ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1529    12281661   27  Unknown
/dev/sda2   *        1530       15979   116068352    6  FAT16
/dev/sda3           15979       16810     6668160    7  HPFS/NTFS
/dev/sda4           16811       30401   109169707+   5  Extended
**[COLOR="Blue"]/dev/sda5           16811       29843   104687541   83  Linux[/COLOR]**
/dev/sda6           29844       30401     4482103+  82  Linux swap / Solaris

/dev/sda5 is the one you want to mount to / while /dev/sda6 is your swap partition.

---

### Post by hibajugalala on 2009-01-10
Should i delete the partition?
or how should i edit it?
I don't wanna screw up this pc...i just got it

---

### Post by solomonhomicz on 2009-01-10
I also messed up my ubuntu. I am dual booting with XP. Right now Ubuntu 8.04 will only run about a minute before total system shutdown (if you're fast you might be able to open a terminal and type two commands), I went to reinstall with the live cd and I experienced total system shutdown just at the time when I reached the partitioning gui in the installer (right after selecting time zone).


There are two kernel versions listed in the grub menu at startup and both crash the same. I went to a wifi spot to update after the original installation (which worked great barring some initial troubles with dialup) and after much hair pulling acguired a connection, I was forced to leave and stop the update download, after this the problems started when I restarted and went to connect the wireless drivers were gone and then crash. Now it crashes no matter what.

Any suggestions? My computer: Toshiba M35X, 1.5g Intel Celeron M, Atheros wifi, 160g samsung HD, 1g RAM (XP is the first OS loaded on the hard drive, but is shown as "Other Operating System:" in the grub menu)

A comprehensive How-To on the grub bootloader would be cool.

Good Ubunday

---

### Post by taurus on 2009-01-10
> **hibajugalala said:**
> Should i delete the partition?
or how should i edit it?
I don't wanna screw up this pc...i just got it

I thought you want to reinstall Ubuntu on top of the same partition that you had Ubuntu before?

---

### Post by hibajugalala on 2009-01-10
ye oh true...i thought i had to edit it in someway

---

### Post by hibajugalala on 2009-01-10
Thank you all so very much!!!

Thank you taurus for helping me :)

---

### Post by solomonhomicz on 2009-01-10
That was the plan but part way through the instllation dialouge my computer shuts down, turns off instantly and unexpectedly.
This is picking the install option imediately after the cd first boots. I'm going to try starting up ubuntu from the live cd and then try to install.

I'm a little leery of this problem because eveytime my computer crashes there's one hell of a clunk from the hard drive.

---

### Post by raunhar on 2009-01-12
I am also trying to reinstall UBUNTU 8.10 . Win XP is already there as I need a dual boot machine. When i go to manual partition, i select the partition on which UBUNTU was installed. How Do I format that particular partition through the installer CD. 
There are three partitions on the disk: NTFS for Win XP, FAT32 for backup disk and the unknow partition for ubuntu.

Pl. suggest

---

