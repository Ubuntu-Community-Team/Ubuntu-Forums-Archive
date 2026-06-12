---
title: "cannot install windows after install Ubunto 8.10"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by keepsimple on 2009-10-11
Hi, 

First just to clarify, I am a fan of Ubuntu Linux, but I need to install Windows on one of my Ubuntu laptop. Hopefully this is a good place to ask about my question. 

I have installed Ubuntu Linux 8.10 on my Thinkpad T41 for a while, and I am very happy with it. But now I need to lend my laptop to my parents for a few months and they need to use Windows (XP or 7).

Since I used the whole disk for Ubuntu when I installed it, the default windows recovery partition is already removed from my laptop. 

Yesterday I tried both Windows XP and Windows 7 RC. But for some reason, Windows XP cannot boot after the install, and Windows 7 RC cannot even find the hard disk to install.  I believe the hard disk is okay because I can re-install Ubuntu back.

I am wondering if Ubuntu does anything special with the hard disk so that Windows cannot boot it / find it sometime, and if there is a workaround for this issue. 

Thanks in advance.

---

### Post by mechro on 2009-10-11
How are you installing Windows?

---

### Post by raymondh on 2009-10-12
> **keepsimple said:**
> Hi, 

First just to clarify, I am a fan of Ubuntu Linux, but I need to install Windows on one of my Ubuntu laptop. Hopefully this is a good place to ask about my question. 

I have installed Ubuntu Linux 8.10 on my Thinkpad T41 for a while, and I am very happy with it. But now I need to lend my laptop to my parents for a few months and they need to use Windows (XP or 7).

Since I used the whole disk for Ubuntu when I installed it, the default windows recovery partition is already removed from my laptop. 

Yesterday I tried both Windows XP and Windows 7 RC. But for some reason, Windows XP cannot boot after the install, and Windows 7 RC cannot even find the hard disk to install.  I believe the hard disk is okay because I can re-install Ubuntu back.

I am wondering if Ubuntu does anything special with the hard disk so that Windows cannot boot it / find it sometime, and if there is a workaround for this issue. 

Thanks in advance.

As mentioned ... how are you installing windows?  I believe you have to create the space and have it formatted already (NTFS, my suggestion).  Then during the windows install, highlight the appropriate space/partition to install unto.

After a successful windows install, don't forget to re-install GRUB.

Back-up your files.

Regards,

---

### Post by N4zgu1 on 2009-10-12
You have to boot with the ubuntu live cd, resize ubuntu and create a ntfs partition for windows, then you install windows in that partition, after that you boot with the ubuntu live cd again to restore grub

---

### Post by Bartender on 2009-10-12
Maybe your parents need to get on board...My 80+ year old father is using Ubuntu!!

---

### Post by keepsimple on 2009-10-14
> **mechro said:**
> How are you installing Windows?

For Windows 7 RC,  I just booted the laptop with Windows 7 CD, and then I expect it will find a disk with unknown partition (Ext3). Then I will re-format it to NTFS. 

However, the problem is that Windows 7 installer cannot even find the disk. It says there is no drive. 

For Windows XP, it is a bit different. It can find the drive, and can re-format it to NTFS. However, after the install, I restart the laptop then it cannot boot (sorry I did not write down the error message. Should have copied it here)

---

### Post by keepsimple on 2009-10-14
> **N4zgu1 said:**
> You have to boot with the ubuntu live cd, resize ubuntu and create a ntfs partition for windows, then you install windows in that partition, after that you boot with the ubuntu live cd again to restore grub


Sounds a good idea. I will try this. Thanks.

---

### Post by Bucky Ball on 2009-10-14
> **keepsimple said:**
> For Windows 7 RC,  I just booted the laptop with Windows 7 CD, and then I expect it will find a disk with unknown partition (Ext3). Then I will re-format it to NTFS. 

No. Windows will NOT deal with EXT partitions. It just calls them 'unknown' and doesn't deal with them in any way, shape or form. As mentioned, you need to use Partition Editor (Gparted) while booted from a LIVE CD to resize and EXT partition.

Once you have done all of this you will, of course, need to tweak your Grub menu to be able to find the Windows partition. (map the partition)

Easiest? Wipe the drive. Install Windows on a partition (preferably the first and a primary partition) leaving the rest of the disk free space. Install Ubuntu. Grub will/should pick up the Windows install and add it automatically.

---

### Post by keepsimple on 2009-10-15
> **Bucky Ball said:**
> No. Windows will NOT deal with EXT partitions. It just calls them 'unknown' and doesn't deal with them in any way, shape or form. As mentioned, you need to use Partition Editor (Gparted) while booted from a LIVE CD to resize and EXT partition.

Once you have done all of this you will, of course, need to tweak your Grub menu to be able to find the Windows partition. (map the partition)

Easiest? Wipe the drive. Install Windows on a partition (preferably the first and a primary partition) leaving the rest of the disk free space. Install Ubuntu. Grub will/should pick up the Windows install and add it automatically.


The problem is that Windows 7 RC does not even recognize the hard disk at all.  I.e. even not "Unknown".  

During the Windows 7 RC installation, the partition list is empty ! 

( i will be more than happy the wipe out the whole drive, and re-install Ubuntu _after_ installing the windows. But it's just not possible given Windows does not recognize the disk. ]

---

### Post by BenAshton24 on 2009-10-15
Make sure that you delete "all" of the partitions, using the windows XP partition editor thing on the installation. Delete all partitions, and then create a new NTFS partition, do a full format when it asks if you want to do a "quick" or "full" format and then install windows. Now when you reboot it should all work perfectly.

---

### Post by Bucky Ball on 2009-10-15
Boot from the Live CD and get into Partition Editor (Gparted). Wipe the lot.

Install Windows on a primary partition. Leave the rest free space. Get a pencil and paper and divide up the drive just how you want it. Install Ubuntu and when you get there, go 'manual partitioning'. Some people panic about manual partitioning but when you get to that part, the Windows install is visibly there showing as a partition. Just don't touch it. Deal with the free space (and you will see that too).

[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

---

