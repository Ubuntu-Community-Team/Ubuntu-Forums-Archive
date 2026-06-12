---
title: "how to format 3TB external USB drive"
date: 2016-02-01
forum: Hardware
---

### Post by alain.roger on 2016-02-01
Hi,

i have external USB drive 3TB...in fact i have several 2TB and 3TB.

unfortunately in gparted it shows only 746GB partition.
gdisk do the same....

i read several different things and i do not know what is the right one to achieve what i want....so to format those external USB disk to 2TB and 3TB.
first thing i read was about having a 64bits USB driver install on my ubuntu 15.10 x64... i thought that i already had such 64bits driver as my OS is a x64.
Next thing i read was about having UEFI in my bios.... but what is the link with external USB drive ???

so please, can you tell me what i must really do to solve my issue ?
thx

---

### Post by oldfred on 2016-02-01
Post this for each drive, sdb, sdc etc what ever they are:
 sudo parted /dev/sda unit s print
sudo gdisk -l /dev/sda

How did you partition drives? You have to have gpt for drives over 2TiB.

UEFI or BIOS should not make a difference. But UEFI normally uses gpt regardless of drive size.

Some older drive caddys do not support larger drives, some SSD, gpt or USB3. And often they are not clear on what exactly they do support. They should work with all drives.

---

### Post by yoshii on 2016-02-01
Actually, from what I remember MBR BIOS has a maximum of 2 Terabye partition sizes.  Double check to make sure.

---

### Post by Vladlenin5000 on 2016-02-01
> **yoshi2 said:**
> Actually, from what I remember MBR BIOS has a maximum of 2 Terabye partition sizes.  Double check to make sure.

Indeed and that's exactly what was mentioned by oldfred in the post before yours:
> You have to have gpt for drives over 2TiB.

---

### Post by alain.roger on 2016-02-02
> **oldfred said:**
> Post this for each drive, sdb, sdc etc what ever they are:
 sudo parted /dev/sda unit s print
sudo gdisk -l /dev/sda

How did you partition drives? You have to have gpt for drives over 2TiB.

UEFI or BIOS should not make a difference. But UEFI normally uses gpt regardless of drive size.

Some older drive caddys do not support larger drives, some SSD, gpt or USB3. And often they are not clear on what exactly they do support. They should work with all drives.

Hello oldfred,

for sur i use a GPT as i need to access to more than 2TB... but if i was able to see 2TB i would be very happy....so here are the information:
first of all HDD 3TB is a WD 30EZRX connected to laptop USB2.0 using adapter. The adapter is ok as i already formated and created partition 2TB and 3TB under windows 7 x64.
so it is recognized as sdd. Result of a 'sudo fdisk -l'```
Disk /dev/sdd: 746.5 GiB, 801569726464 bytes, 1565565872 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 782E9864-45C4-42FB-9BA8-CB0B0F603916

Device     Start        End    Sectors   Size Type
/dev/sdd1   2048 1565564927 1565562880 746.5G Microsoft basic data
```

here is the result of a 'sudo parted /dev/sdd unit s print'
```
alain@ntb0001:~$ sudo parted /dev/sdd unit s print
Model: WDC WD30 EZRX-22D8PB0 (scsi)
Disk /dev/sdd: 1565565872s
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start  End          Size         File system  Name  Flags
 1      2048s  1565564927s  1565562880s  ntfs               msftdata
```

and here result of a 'sudo gdisk -l /dev/sdd'
```
GPT fdisk (gdisk) version 1.0.0

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 1565565872 sectors, 746.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 782E9864-45C4-42FB-9BA8-CB0B0F603916
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1565565838
Partitions will be aligned on 2048-sector boundaries
Total free space is 2925 sectors (1.4 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      1565564927   746.5 GiB   0700  
```

---

### Post by oldfred on 2016-02-02
I believe this is the problem, but not sure of answer.
 Sector size (logical/physical): 512B/512B

Almost all new drives are 512/4K.
If it was an internal drive I would say check for IDE, when it should be AHCI. But neither are used with USB drives. And I think it is the caddy or something related.

You did say Windows saw it as 2.8TB?
When we saw issue before it was the USB adapter. And user purchase new one that specifically said it supported large drives, which solved issue.


 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

---

### Post by yoshii on 2016-02-03
> **Vladlenin5000 said:**
> Indeed and that's exactly what was mentioned by oldfred in the post before yours:

sorry, i didn't mean to provide redundant info.  I don't read every single reply when reading threads.  
at least theres some consensus on the issue though.

---

### Post by Yellow Pasque on 2016-02-04
Do you really need one huge partition? If you could carve it up into two 1.5 TB partitions and format it as MBR instead of GPT, that would probably be the easiest way and allow you to use the drive on older systems.

> Next thing i read was about having UEFI in my bios.... but what is the link with external USB drive ???

I think that mainly concerns booting from the drive.

---

### Post by oldfred on 2016-02-04
With MBR you still cannot have more than 2TiB, regardless of the number of partitions.
And if system is UEFI, best to always have all drives as gpt. I even now have gpt on most of my flash drives, except some installers.
       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

---

### Post by Yellow Pasque on 2016-02-04
> **oldfred said:**
> With MBR you still cannot have more than 2TiB, regardless of the number of partitions.

Thanks for the correction. I'm stills stuck in the age of BIOS and MBR with my hardware...

---

