---
title: "Seagate USB drive not mounting at all"
date: 2007-03-19
forum: Hardware &amp; Laptops
---

### Post by mightyteegar on 2007-03-19
Running Edgy and I have a Seagate 80GB external USB drive (called "phoenix") with about 70GB worth of media on it that I want to move off.  Here's my troubleshooting process.

Background: I have another Seagate 160GB drive ("genesis") that automounts just fine.  I also have a SanDisk Cruzer Micro flash drive that works perfectly.  "phoenix" has worked on this machine before, running Ubuntu Edgy and Dapper and, before Ubuntu, MEPIS.  

This drive is not listed in my /etc/fstab.

When I plug it in and turn it on the drive is detected by the system:

```
user-janus ~ >lsusb
Bus 005 Device 008: ID 0781:5406 SanDisk Corp. 
[COLOR="Red"]Bus 005 Device 007: ID 0bc2:0503 Seagate RSS LLC [/COLOR]
Bus 001 Device 005: ID 413c:3200 Dell Computer Corp. 
Bus 001 Device 004: ID 413c:2005 Dell Computer Corp. 
Bus 004 Device 002: ID 0f30:0107 Jess Technology Co., Ltd 

```

and fdisk sees it:

```
user-janus ~ >fdisk -l            

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   [COLOR="Red"]Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    b  W95 FAT32[/COLOR]

Disk /dev/sdc: 1027 MB, 1027416576 bytes
16 heads, 63 sectors/track, 1990 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1991     1003305    e  W95 FAT16 (LBA)

```

I have a desired mount point /mnt/phoenix that is created with proper permissions.

Mounting the drive doesn't work:

```
user-janus ~ >sudo mount -t vfat /dev/sdb1 /mnt/phoenix
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

user-janus ~ >sudo mount -t auto /dev/sdb1 /mnt/phoenix
mount: you must specify the filesystem type
user-janus ~ >sudo mount -t msdos /dev/sdb1 /mnt/genesis
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmesg gives this worrying error message:

```
[17182892.136000] FAT: bogus number of reserved sectors
[17182892.136000] VFS: Can't find a valid FAT filesystem on dev sdb1.

```

Tried to fsck the drive and:

```
user-janus ~ >sudo fsck.vfat /dev/sdb1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 133.

```

133 VFATs?!  Anyway, I do not have a Windows partition to test this drive on and now I'm worried that it's corrupted, but that seems fairly ridiculous because it mounted just fine running Ubuntu in the past.  The last time I mounted it was about two months ago and it worked (running Edgy).  Since then it has sat powered off and not plugged in until tonight. The aforementioned "genesis" drive also automounted under Dapper and MEPIS and continues to mount fine.  

UPDATE: I booted my system using SLAX 5.1.8 LiveCD and phoenix mounted perfectly -- I could browse the drive and open the files on it.  

What is going on here?  How can I get the data off this drive?

---

### Post by apjone on 2007-03-19
Use the live cd and copy the data to where you want to keep it.

---

### Post by mightyteegar on 2007-03-19
Looks like I have no choice but to do that.  Still, I'm curious -- why isn't Ubuntu properly recognizing and mounting this drive?

---

### Post by apjone on 2007-03-19
not sure, be nice to find out why. is there anything above the 2 lines in dmeg that you posted .

](*,) ](*,) ](*,)

---

### Post by mightyteegar on 2007-03-20
> not sure, be nice to find out why. is there anything above the 2 lines in dmeg that you posted .

Yes, those same two lines about twenty times. :)  But no, there was no other output that differed from what I get from plugging in "genesis", just those two lines.  

I finally ended up using SLAX to copy the files off phoenix to genesis and then reformatting phoenix (as FAT32, and strangely Ubuntu has no problems recognizing it now).  However, now I'm a little nervous that when I upgrade to Feisty in a couple of months that it will become unreadable again.  

Weirdness.

---

