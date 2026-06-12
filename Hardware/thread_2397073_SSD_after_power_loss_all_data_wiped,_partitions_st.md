---
title: "SSD after power loss: all data wiped, partitions still intact"
date: 2018-07-25
forum: Hardware
---

### Post by Matyy on 2018-07-25
My notebook crashed, and no ctrl+alt+del nor REISUB helped. I had to take its power away. After that it wouldn't boot any more. 

It also wouldn't boot into windows, when choosing it directly from the uefi boot menu. 

After booting with a usb stick i can see following:
- all partitions are still there 
- the mounted linux partition is completely empty, no folders, no files. 
- can't mount windows partition, because its not cleanly unmounted. My windows was already set up to fully shut down. It should be mountable 

I ran fsck on a DD'ed image of the EXT4 partition. There where a bazillion of errors. -p didn't even start, after running it with -y, it took a few hours and afterwards i had a lot of entries in lost and found. Mostly numbers. 

Photorec seems to be able to recover stuff. 

I have backups, but I've been on holidays for a week and with the bad internet connection here, i couldn't backup. 

This happened before. But two years ago. Since than i was very hesitant to force power off my system I think i was to quick this time.

I'm mostly curious how this could have happened.

The windows partition wasn't even mounted. 

It's a liteon m2 ssd in a four year old alienware 13.
The linux partition is one ext4 partition, no separated boot nor home. 

Any ideas? I made a dd copy of the full disk now. Two years ago i tried to fix the partition table with testdisk. Without success. But actually it doesn't look broken.

---

### Post by Autodave on 2018-07-25
Do you know if Windows installed any updates right before this happened?  I have seen Win updates wipe out Linux installs.

---

### Post by Matyy on 2018-07-25
No, I haven't booted into windows for weeks.

---

### Post by oldfred on 2018-07-25
Windows updates are in back ground and if a major update, it turns fast start up back on.
So even if weeks ago that could be Windows issue.

But hard shutdown should not totally erase ext4 partition. It may damage it and then fsck can repair it, if ext4 and therefore has journal. 

Post this:
sudo parted -l
sudo gdisk -l /dev/sda

---

### Post by Matyy on 2018-07-31
I couldn't continue until now:
I am running a photorec on it now. Want to see how much it will restore.


gpart:
```
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 500118192 sectors, 238.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 479AE3B4-6EF0-4A69-9D48-1ADF052EFA1F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 500118158
Partitions will be aligned on 2048-sector boundaries
Total free space is 2669 sectors (1.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1050623   512.0 MiB   EF00  EFI System Partition
   2         1050624       312725503   148.6 GiB   8300  
   3       312725504       312987647   128.0 MiB   0C01  Microsoft reserved ...
   4       312987648       483520511   81.3 GiB    0700  Basic data partition
   5       483520512       500117503   7.9 GiB     8200  
```

parted, in german, tho:
```
Modell: ATA LITEONIT L8T-256 (scsi)
Festplatte  /dev/sdb:  256GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: gpt
Disk-Flags: 

Nummer  Anfang  Ende   Größe   Dateisystem  Name                          Flags
 1      1049kB  538MB  537MB   fat32        EFI System Partition          boot, esp
 2      538MB   160GB  160GB   ext4
 3      160GB   160GB  134MB                Microsoft reserved partition  msftres
 4      160GB   248GB  87,3GB  ntfs         Basic data partition          msftdata
 5      248GB   256GB  8498MB
```

---

