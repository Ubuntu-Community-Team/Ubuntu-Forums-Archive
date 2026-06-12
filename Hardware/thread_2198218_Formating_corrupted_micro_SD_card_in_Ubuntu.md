---
title: "Formating corrupted micro SD card in Ubuntu"
date: 2014-01-07
forum: Hardware
---

### Post by kzagko on 2014-01-07
Hi guys,

I have an 8GB micro SD Transent card that was working fine until a month ago. Last month when I pluged into my laptop it did not mount or get detected. I followed instruction on hoe to use testdisk tool and simmilar command line commands and programs and finally managed to get it seen by my laptop. It stilll does not mount and also it only reposrts 1GB in size. I cannot format it or access it any way. I tried playing aroung with testdisk but no result. I even tried using dd to copy/clone another micro sd card of the same size to this one but nothing happened. Since I searched a lot of forums and tried a lot of things I am posting here in case anyone is able to help me out. Details about my card and system are below.


Ubuntu 13.04 64-bit
8GB micro SD Transent card
testdisk reports
Disk /dev/mmcblk0 - 1073 MB / 1024 MiB - CHS 32768 4 16


Let me know if you need more information and if there is anything I can try.

---

### Post by tfrue on 2014-01-07
I would like to see the ouput of:

```
sudo fdisk -l
```
and 
```
lsblk
```

with the sd cards plugged in

---

### Post by electrohandyman501 on 2014-01-07
How old is the card. They don't last forever, the more you write to them the shorter their life. Way less than a hard disk. 
My opinion----just replace it. It's only $12 from Amazon.........

---

### Post by kzagko on 2014-01-08
Hi the output of 

sudo fdisk -l
is

Disk /dev/mmcblk0: 1073 MB, 1073741824 bytes
4 heads, 16 sectors/track, 32768 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mmcblk0 doesn't contain a valid partition table


and of lsblk is 

NAME    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda       8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1    8:1    0   100M  0 part /media/System_Reserved
&#9500;&#9472;sda2    8:2    0  58.5G  0 part 
&#9500;&#9472;sda3    8:3    0     1K  0 part 
&#9500;&#9472;sda5    8:5    0    67G  0 part /media/Extension
&#9500;&#9472;sda6    8:6    0   7.5G  0 part [SWAP]
&#9492;&#9472;sda7    8:7    0 332.8G  0 part /
sr0      11:0    1  1024M  0 rom  
mmcblk0 179:0    0     1G  0 disk



The card is roughly 7 months old and I have only used it in my camera so it is not like I have been writting/reading on it for ever. Plus I believe the life expectansy of these cards is of the order of millions of read/writes.


Thanks

---

### Post by tfrue on 2014-01-08
Hmm... I'm not sure why it's only showing 1GB, but what you can try to do is use fdisk and re create a new MBR partition. **THIS WILL ERASE EVERYTHING**. Just to let you know, but I don't think there is much we can do for recovery anyway.  

Type:```
sudo fdisk /dev/mmcblk0
d
1
d # Use 'd' again if you have more partitions to delete
n
p
1
enter
enter
enter
t
7 #should make it an NTFS FS type
p # Make sure the partition is there and says NTFS under TYPE.
w #To write the changes!

```

Now we need to create a FS, so use mkfs.

 Type:```

sudo mkntfs /dev/mmcblk0p1
```

Give it some time and it should be ready to use!

Good Luck, 
Chris

---

### Post by kzagko on 2014-01-08
Hi Chris,

First of all thank you for taking time to look into this.

I have tried this before but I am doing it again to make sure. I have just run the commands as you recommended to create a new MBR with fdisk but the write took ages too finish and finally failed. I am attaching the output below, it was stuck at "The partition table has been altered!" for 10 minutes before reporting that it failed. This happened also when I was trying to use the testdisk utillity which took nearly 30 minutes and then failed. can you suggest a work around this?

```
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x056da3dd.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): d
No partition is defined yet!

Command (m for help): 1
1: unknown command
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the DOS compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): d
No partition is defined yet!

Command (m for help): n
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): p
Partition number (1-4, default 1): 1
First sector (2048-2097151, default 2048): 
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-2097151, default 2097151): 
Using default value 2097151

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 7
Changed system type of partition 1 to 7 (HPFS/NTFS/exFAT)

Command (m for help): p

Disk /dev/mmcblk0: 1073 MB, 1073741824 bytes
4 heads, 16 sectors/track, 32768 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x056da3dd

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1            2048     2097151     1047552    7  HPFS/NTFS/exFAT

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 5: Input/output error.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)

Error closing file


```

I believe that the number of the cylinders or their size might have changed thus causing the shrinkage in size.

---

### Post by tfrue on 2014-01-08
Well, you can try and fix those and see if that helps, but you may be in the same boat as me a little while ago. I had a usb that I was using Universal USB Installer to install 13.10 and towards the end it just stopped. I did everything I could to try and save the drive, but nothing worked simply because there is a read write error with the drive. It's dead. It's impossible to mount the drive, or change anything with fdisk, or any partitioning software because of the read write error. 

So I said all of that to say I can go through the same troubleshooting steps with you that I did, but it may end up being time wasted.

But to help you with wanting to change the cylinders, type:
```
sudo fdisk /dev/mmcblk0
x
c
enter

```
This will take the default entry for your drive, and I would try that first before entering a random number.

You could also take the default on the number of heads, and the number or track sectors, if you want.

Type: ```

(from the expert prompt)
h
enter
s
enter
```

Good luck, and I'll be waiting for your response
Chris

---

### Post by kzagko on 2014-01-10
Hi my bad luck continues. the last 3 hours I am not able to even see the /dev/mmcblk0 . I will try to put the micro sd on a usb reader to see if I can access it from there. This is the output of 

sudo tailf /var/log/syslog


Andromeda kernel: [  736.819944] mmc0: error -110 whilst initialising SD card
Jan 10 17:38:50 Andromeda kernel: [  736.823393] sdhci-pci 0000:0d:00.0: Will use DMA mode even though HW doesn't fully claim to support it.

I will keep trying but I guess there is no way to revive this as you mention on your reply. I am just baffled by the fact that these cards given that they have no moving parts die that easy. I always thought in the worst case scenario you could use dd to rewrite the MBR or any other information necessary to fix them.  Thanks again for you time I will let you know when I have news.

---

### Post by tfrue on 2014-01-10
It's not necessarily the card's fault, nor yours, that it's dead. Sometimes things just happen with software or whilst reading/writing to the disk that cause errors. I'm still holding on to mine and I play with it occasionally just to see if maybe it will work, but it probably wont.

You can do some research in the man pages and online for the 'dd' command because I don't know how to use it.

Good Luck,
Chris

---

### Post by tgalati4 on 2014-01-10
Try formatting it in a camera.  Then see if it will mount.

---

### Post by kzagko on 2014-01-15
I have tried to put it in my camera and my cell phone but nothing happened. I played a bit more with dd if=/dev/zero of=/dev/mmcblk0 and managed to get the card showing a size of 2 GB this time instead of 1. But still it is not able to get mounted or get any new partition on it. I will keep trying and post here any new results. If you have any ideas please let me know.

---

### Post by rod4 on 2014-10-17
> **tfrue said:**
> Hmm... I'm not sure why it's only showing 1GB, but what you can try to do is use fdisk and re create a new MBR partition. **THIS WILL ERASE EVERYTHING**. Just to let you know, but I don't think there is much we can do for recovery anyway.  

Type:```
sudo fdisk /dev/mmcblk0
d
1
d # Use 'd' again if you have more partitions to delete
n
p
1
enter
enter
enter
t
7 #should make it an NTFS FS type
p # Make sure the partition is there and says NTFS under TYPE.
w #To write the changes!

```

Now we need to create a FS, so use mkfs.

 Type:```

sudo mkntfs /dev/mmcblk0p1
```

Give it some time and it should be ready to use!

Good Luck, 
Chris

    Thanks Chris! Worked for me and saved a 4 gig SD card.... Just joined so I will be visiting often and I run Ubuntu 14.04 LTS   Rod

---

