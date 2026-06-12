---
title: "dual boot partition problems"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by delbooh on 2009-10-23
I'm trying to make a dual boot Vista/Ubuntu on my new laptop. I've shrunk the main windows partition and made 106 Gb of free space for Ubuntu. \the problem is that the hard disk seems to be already partitioned into 4 partitions and Gparted wont let me make another partition in the  unused space. does anyone know how i can find out what these partitions are for and which one i could safely remove without messing up windows? I can see all 4 in the disk management tool in windows, but not sure what is on them.

---

### Post by dvlchd3 on 2009-10-23
First of all, be extremely careful when resizing Vista partitions.  Vista does not play nice with GParted...
[http://ubuntuforums.org/showthread.php?t=404200](http://ubuntuforums.org/showthread.php?t=404200)

Secondly, depending on the manufacture, one of these partitions may be for the recovery discs.  Most modern laptops do not ship with the recovery discs, and you need to create them yourself.  If you have already done this, you can delete that partition/use that partition.

Can you post the results from the below command while in Ubuntu live CD.  This will show us how your hard drive is currently partitioned.

```

sudo fdisk -l

```

---

### Post by Bartender on 2009-10-23
We can't tell you what the partitions are.  You have the laptop.  What brand and model is it?  How does Vista identify the partitions?  Generally, after you've made your recovery discs you can wipe the recovery partition but I'd want to make absolutely sure that was true in your case

---

### Post by delbooh on 2009-10-23
here is the result of fdisk -l:
 
disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors, 48641 cylinders
units= cylinders of 16065 * 512 = 8225280 bytes
disk identifier: 0x24fa2fe4
 
device boot     start     end           blocks          id     system
/dev/sda1         1         192         1536000        27   unknown
partition 1 does not end on cylinder boundary
/dev/sda2 *      192      32556     259969020     7     hpfs/ntfs
/dev/sda3      46413     47534     9006080         7     hpfs/ntfs
/dev/sda4      47534     48642     8899584         17   hidden hpfs/ntfs
 
My laptop is a toshiba, and I have created the recovery disks already.

---

### Post by presence1960 on 2009-10-23
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by delbooh on 2009-10-24
I might have missed something, I was typing out by hand because I couldn't get internet connectivity in Ubuntu last night. Here is the results again:
 
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24fa2fe4
 
 
   
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       32556   259969020    7  HPFS/NTFS
/dev/sda3           46413       47534     9006080    7  HPFS/NTFS
/dev/sda4           47534       48642     8899584   17  Hidden HPFS/NTFS
Disk 
/dev/sdb: 14 MB, 14909440 bytes
2 heads, 32 sectors/track, 455 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x00000000
   
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         455       14531+   1  FAT12

---

