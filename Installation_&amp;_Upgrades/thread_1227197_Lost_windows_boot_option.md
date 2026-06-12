---
title: "Lost windows boot option"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by kmskjorestad on 2009-07-30
HI! I reasently installed ubuntu on a computer where i had Windows vista installed before. Now i cant boot windows. I have tried editing menu.lst and added the following: 

title        Windows Vista
root        (hd0,0)
makeactive
chainloader    +1
boot

But i cant boot vista. Any ideas? Think I have windows on sdb01, se under:

[php] karlm@Km.....:~$ sudo fdisk -l
[sudo] password for km....: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22af22af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23570   189325993+  83  Linux
/dev/sda2           23571       24321     6032407+   5  Extended
/dev/sda5           23571       24321     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c42da43

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       31871   256000000    7  HPFS/NTFS
/dev/sdb2           31871       60802   232384512    7  HPFS/NTFS
[/php]
[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

---

### Post by merlinus on 2009-07-30
Try this:

title Windows Vista
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

---

### Post by kmskjorestad on 2009-07-30
Doesn`t work... :-( 
 
gets the following message:
 
Starting up ...
 
BOOTMGR missing
Press ctrl+Alt+Del to restart

---

### Post by merlinus on 2009-07-30
Is vista on sdb1 or sdb2?  One of these may be a recovery partition.

---

### Post by stlsaint on 2009-07-30
are you sure you didnt overwrite that partition by accident?

---

### Post by merlinus on 2009-07-30
@stlsaint

Look at the results of sudo fdisk -l and it will be quite obvious that he did not. Both sdb2 and sdb1 are formatted as ntfs.

---

### Post by kmskjorestad on 2009-07-30
Windows vista is there, thats for shure. Seems like im missing some boot up files. Im now trying to fix windows while booting from the windows installation dvd

---

### Post by kmskjorestad on 2009-07-31
Have not manage to fix it yet! Booting windows vista dvd did not work. I saw the vista files from a menu, but the repeare option did not manage to find the OS to fix. I was asked to upload the drivers for my hard drive if my OS wheren`t listed. I did not find any hard drive drivers,......... so here I am. I know i have the c: partison with vista installed but i can not boot. 
 
Maby some history will help:
 
Before this i had wista installed on the sdb disk, and xp and ubuntu installed on the sda disk. Then I used grub bootloader. What causes this tread was that I reeinstalled ubuntu on the entire sda disk, and now cant boot the vista os on sdb disk. It missing BOOTMGR.
 
Any ideeas where and how to find BOOTMGR?:D

---

### Post by merlinus on 2009-07-31
Try supergrub

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by kmskjorestad on 2009-07-31
Did not work, tried ewery option. Im nerby giving up. The only message i receve is BOOTMSG is missing...... :-(

---

### Post by merlinus on 2009-07-31
This may be useful:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by louieb on 2009-07-31
> **kmskjorestad said:**
> 
```
 karlm@Km.....:~$ sudo fdisk -l
[sudo] password for km....: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22af22af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23570   189325993+  83  Linux
/dev/sda2           23571       24321     6032407+   5  Extended
/dev/sda5           23571       24321     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c42da43

   Device [COLOR=Red]Boot[/COLOR]      Start         End      Blocks   Id  System
[COLOR=Red]/dev/sdb1               1       31871   256000000    7  HPFS/NTFS[/COLOR]
/dev/sdb2           31871       60802   232384512    7  HPFS/NTFS

```> **merlinus said:**
> Try this:

title Windows Vista
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

This should work but one thing is missing -  the** boot flag needs to be set **on partition sdb1.  Linux doesn't care if its set or not. But windows does. Gparted (System>Adminstration>Partition Editor can set it) Right click on partition select flags. 


IF you still get boot file missing then you should be able to find something for vista. Believe MS has a recovery CD you can download. [How to fix XP when the boot files are missing - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=813628")

---

