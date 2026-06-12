---
title: "Hard drive problems"
date: 2010-05-03
forum: Hardware
---

### Post by gizmoguy1 on 2010-05-03
I updated to 10.04 a couple of days ago, I only started getting this problem today.

After a very short amount of time being logged in, 2 of my hard drives stop working. I have 5 750GB hard drives, 1 has / and swap on it, the others are for data, but I am only using the first to at the moment. Nautilus shows no files in these 2 hard drives, but the other 2 are fine, as is the system disk. Here's what I'm getting in dmesg over and over again...

```

[ 2377.833672] end_request: I/O error, dev sdb, sector 4007
[ 2377.833689] sd 9:0:0:0: [sdb] Unhandled error code
[ 2377.833695] sd 9:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2377.833708] sd 9:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 0f a7 00 00 08 00
[ 2377.833745] end_request: I/O error, dev sdb, sector 4007
[ 2377.833767] sd 9:0:0:0: [sdb] Unhandled error code
[ 2377.833774] sd 9:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2377.833784] sd 9:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 0f a7 00 00 08 00
[ 2377.833820] end_request: I/O error, dev sdb, sector 4007
[ 2414.775081] sd 9:0:0:0: [sdb] Unhandled error code
[ 2414.775083] sd 9:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2414.775086] sd 9:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 41 00 00 02 00

```I have tried unmounting and remounting the drives, but I cannot remount:

```

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```and in dmesg:

```

[ 2840.396365] sd 10:0:0:0: [sdc] Unhandled error code
[ 2840.396367] sd 10:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 2840.396369] sd 10:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 41 00 00 02 00
[ 2840.396375] end_request: I/O error, dev sdc, sector 65
[ 2840.396381] EXT3-fs: unable to read superblock

```I'm running 64-bit 10.04 with Core 2 Quad @ 2.66GHz, 4GB memeory, nVidia (yes, I know) motherboard.

These drives have a lot of data on them, any help would be greatly appreciated. Thanks.

EDIT: Kernel is 2.6.32-21-generic. Will try with an earlier version and report back.

EDIT 2: Tried mounting with 'sync' option, appears to have fixed it. I think there maky have been a conflict between the OS and disk buffering or something, but sync mode is working, just as fast as before at the cost of a little CPU. Can we keep the thread open, just in case something happens? Thanks.

EDIT 3: Nope, It's just broken again. slightly different dmesg. Any help?

```

[19510.024140] sd 9:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 00 3f 00 00 08 00
[19510.024146] end_request: I/O error, dev sdb, sector 63
[19510.024148] __ratelimit: 1 callbacks suppressed
[19510.024150] Buffer I/O error on device sdb1, logical block 0
[19510.024152] lost page write due to I/O error on sdb1
[19510.024227] sd 9:0:0:0: [sdb] Unhandled error code
[19510.024229] sd 9:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[19510.024231] sd 9:0:0:0: [sdb] CDB: Read(10): 28 00 33 04 01 5f 00 00 08 00
[19510.024237] end_request: I/O error, dev sdb, sector 855900511
[19510.024242] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=26747434, block=106987556
[19510.024321] sd 9:0:0:0: [sdb] Unhandled error code
[19510.024322] sd 9:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[19510.024324] sd 9:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 00 3f 00 00 08 00
[19510.024330] end_request: I/O error, dev sdb, sector 63
[19510.024332] Buffer I/O error on device sdb1, logical block 0
[19510.024334] lost page write due to I/O error on sdb1
[19510.412837] sd 9:0:0:0: [sdb] Unhandled error code
[19510.412840] sd 9:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[19510.412843] sd 9:0:0:0: [sdb] CDB: Read(10): 28 00 31 bc 03 c7 00 00 08 00
[19510.412850] end_request: I/O error, dev sdb, sector 834405319
[19510.412860] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=26076922, block=104300657
[19510.412952] sd 9:0:0:0: [sdb] Unhandled error code
[19510.412953] sd 9:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[19510.412955] sd 9:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 00 3f 00 00 08 00
[19510.412961] end_request: I/O error, dev sdb, sector 63
[19510.412963] Buffer I/O error on device sdb1, logical block 0
[19510.412965] lost page write due to I/O error on sdb1
[19510.413040] sd 9:0:0:0: [sdb] Unhandled error code
[19510.413042] sd 9:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[19510.413044] sd 9:0:0:0: [sdb] CDB: Read(10): 28 00 31 bc 03 c7 00 00 08 00
[19510.413050] end_request: I/O error, dev sdb, sector 834405319
[19510.413056] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=26076922, block=104300657
[19510.413134] sd 9:0:0:0: [sdb] Unhandled error code
[19510.413135] sd 9:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[19510.413138] sd 9:0:0:0: [sdb] CDB: Write(10): 2a 00 00 00 00 3f 00 00 08 00
[19510.413143] end_request: I/O error, dev sdb, sector 63
[19510.413145] Buffer I/O error on device sdb1, logical block 0
[19510.413147] lost page write due to I/O error on sdb1
[19510.789165] sd 9:0:0:0: [sdb] Unhandled error code
[19510.789168] sd 9:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[19510.789171] sd 9:0:0:0: [sdb] CDB: Read(10): 28 00 34 64 01 5f 00 00 08 00
[19510.789178] end_request: I/O error, dev sdb, sector 878969183
[19510.789189] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=27468330, block=109871140
[19510.789281] sd 9:0:0:0: [sdb] Unhandled error code
[19510.789283] sd 9:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK

```

---

### Post by gizmoguy1 on 2010-05-03
Bump.

---

### Post by gizmoguy1 on 2010-05-05
Nobody? =(

---

### Post by gizmoguy1 on 2010-05-06
D=

---

### Post by srs5694 on 2010-05-06
Try using gsmartcontrol (you may need to install it) or some similar utility to check your drives' SMART data. (This is information on drive health that's maintained by the drives themselves.) It's conceivable that your drives are going bad. If two of them are going bad, I'd suspect overheating, but it could be just plain bad luck. If necessary, use the gsmartcontrol utility to run full checks on the disks (this can take a while).

Another possibility is bad or loose cables, so check that.

---

### Post by jstretch on 2010-06-04
I found this thread looking to solve what appears to be an extremely similar if not identical problem. Upgraded to Lucid a couple weeks ago and just started having problems with two of the three drives forming a RAID5 array. They'll work fine for a while, then apparently "die." dmesg gets spammed with the following:

```

[ 8348.775260] sd 5:0:0:0: [sdc] Unhandled error code
[ 8348.775263] sd 5:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 8348.775267] sd 5:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 8348.775276] end_request: I/O error, dev sdc, sector 0
[ 8348.775298] sd 5:0:0:0: [sdc] Unhandled error code
[ 8348.775301] sd 5:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 8348.775305] sd 5:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 10 00 00 00 08 00
[ 8348.775315] end_request: I/O error, dev sdc, sector 4096
[ 8348.778740] sd 5:0:0:0: [sdc] Unhandled error code
[ 8348.778750] sd 5:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 8348.778765] sd 5:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 8348.778813] end_request: I/O error, dev sdc, sector 0
[ 8348.778856] sd 5:0:0:0: [sdc] Unhandled error code
[ 8348.778869] sd 5:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 8348.778881] sd 5:0:0:0: [sdc] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 8348.778928] end_request: I/O error, dev sdc, sector 0

```

These are three identical 2.0 TB drives, not six months old. Running kernel 2.6.32-22.

---

### Post by jstretch on 2010-06-07
Had a third, different drive "fail" yesterday. My USB mouse and keyboard also randomly locked up. This is definitely not a hardware issue.

I read somewhere (can't remember where, sorry) that it might have something to do with an Nvidia SATA controller sharing an IRQ with one of the USB controllers. This hasn't been an issue until upgrading kernel 2.6.31 or .32 (can't recall which was running when the problem first began occurring). My guess is that something was changed in the APIC code.

At any rate, I added 'noapic' to my kernel boot line in grub, and the error hasn't recurred since, though obviously a few days need to pass before any reliable conclusion can be reached.

---

### Post by Mspirit on 2010-06-07
Installed Lucid couple of days ago..Apparently, I've the same problem

Had the problem -also on Lucid- before now on the same Laptop model -Toshiba NB205- before it was stolen...So I'm guessing it's not a hardware problem

The problem:

While working the HDD light flicks as usual...but randomly, sometimes CPU is heavily loaded other times the system is ideal >

The screen freezes..while the mouse still moves without having any effect to it's input..Shortly after the cursor stops and I am left with no option but to hardreset the system...

Plz Help

---

### Post by Mspirit on 2010-06-07
Actually it seems, same problem was there also with ubuntu 9.04

[http://ubuntuforums.org/showthread.php?t=1214356](http://ubuntuforums.org/showthread.php?t=1214356)

Should we start a bug report or what :S

---

### Post by nerdybrunette on 2011-11-02
Did anybody find a solution to this? I'm having the same problem :( 

Here's my thread: [http://ubuntuforums.org/showthread.php?p=11420126#post11420126]("http://ubuntuforums.org/showthread.php?p=11420126#post11420126")

---

### Post by dFlyer on 2011-11-02
Use disk utility to check your drives for bad sectors.

---

### Post by nerdybrunette on 2011-11-03
My OS (Ubuntu 10.04) doesn't see my hard drive at all. Not under fdisk, not in lsusb, not in /dev/sd*... nothing... So I can't check it, unfortunately. :(

---

### Post by larryweeks on 2012-10-09
Ubuntu is causing the problems, I have had to quit using it, up to now it has killed 8 drives. 2 were western digital and the rest seagates all were terabit drives. I have a dual boot and the windows drive is the only one that has survived. 

The problem has something to do with Ubuntu causing the drives to over work and over heat. My new drives lasted 1 day. This needs a fix and I dont know where to get it from.

---

### Post by oldfred on 2012-10-09
Thread closed, necromancy.

@larryweeks
This is an old thread so those issues do not apply to any issues you have. Please start a new thread. I have not heard of issues, but you need to look for bug reports. If you can duplicate the issue then you really need to report it as a bug since developers do not usually participate in the forums. We are all volunteers helping each other.

bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

