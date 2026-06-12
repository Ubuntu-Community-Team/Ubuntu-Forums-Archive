---
title: "Working partition missing in Partition Table"
date: 2015-03-26
forum: Hardware
---

### Post by adele2 on 2015-03-26
Hi, the title of the thread maybe sounds badly, but I think it's true. I just came from notebook repair, where I had only to install new ubuntu nearby Windows installation. When started windows partition manager everything was okay: 
1) System Protected Partition (disk is MBR)
2) Acer Recovery
3) Windows 97GB
4) Documents 340GB
5) Ubuntu 31 GB
unallocated

Okay, so I will just make bootable USB, some steps in wizard and I am done, but after running installer I saw that partitions are... different. 340 GB partitions was called like "unable to use", the tool couldn't add any new or remove existing partition. GParted also listed wrong partitions. Fdisk shown that partition table doesn't seem to be correct, but listed this wrong partition table.  When booted back to Windows everything was fine as always (340gb partition was used for over one year, there is over 191gb of data). All are set as Primary. 
I thought that they are maybe overlapping, but they are not. When I run diskpart in Windows and selected the disk (the only disk at the PC) and listed partitions available the 340gb one was missing, but... it's working on the system.

I think that there might be a problem with partition table, on Saturday maybe I will scan everything using TestDisk, but... what could go wrong? Is there other, good way, to rescan current partitions? What can be done to repair it without moving any data?

---

### Post by Mark Phelps on 2015-03-26
You can't create a Linux filesystem partition in Windows and Disk Management only shows the size of the Linux partitions.  IF you created the Ubuntu partition in Windows, that is NOT going to work.

---

### Post by oldfred on 2015-03-26
And you only can have 4 primary partitions with MBR(msdos) and one of those needs to be the extended partition so you can have logical partitions.
If you attempt to create more than 4 partitions with Windows it converts to dynamic which does not work with Linux, nor with some Windows repair tools.

Post this from Ubuntu live installer's terminal:
sudo parted -l
sudo fdisk -lu

---

### Post by adele2 on 2015-03-27
Ach, I knew that you can understand me wrong...
1) i am not beginner in that, so I created unformatted partition Under Windows! i wanted to format it under ubu Installer/gparted
2) i was aware that you cannot still understand that I don't have access to this pc so I cannot post anything, but I have some knowledge about situation


the ldm problem under ubuntu could be quite obvious, the fact comes further: why this partition was not listed in partition table either under windows diskpart and was still working correctly under this system? Its not about installation, I am trying to figure out how it is possible and how to repair it.


All partitions were primary, There eas not enough space to move data from 340gb partition and make it as extended. Am i right that it is not possible to mark it as extended without deleting partition, am I right?

---------

OH! I know what could be wrong. Last time I was working a lot about small, self-bootable application that can partition GPT drives, that made my thoughts about MBR mistaken. You told me that MBR can have up to 4 Primary partitions, I was thinking that it's 5 (proof is here: [http://thestarman.pcministry.com/asm/mbr/PartTables.htm](http://thestarman.pcministry.com/asm/mbr/PartTables.htm), it's 4) . Also I realized (under the shower ^^) that between recovery partition and c there was also something (no clue what was that).
The very basic solution for this is: remove Recovery partition and this something, shift everything left, create extended partition and one logical inside for Ubu. That could do the trick.

One question remains unanswered: WHY 5th Primary partition (340gb) was working under Windows without problems over a year and was not listed under partition table? For linux it was problem to treat this space as partition and he checked it as "unable to use".

---

### Post by oldfred on 2015-03-27
Please post info requested in post #3, so we all know what partitions you do have.

---

### Post by adele2 on 2015-03-27
Okay, solved. I don't want repeat myself why I cannot do this.

---

