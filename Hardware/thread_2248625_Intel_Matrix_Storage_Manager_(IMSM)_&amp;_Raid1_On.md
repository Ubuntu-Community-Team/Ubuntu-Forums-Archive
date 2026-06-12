---
title: "Intel Matrix Storage Manager (IMSM) &amp; Raid1 On Non-OS Storage Only Disk Always Resync"
date: 2014-10-15
forum: Hardware
---

### Post by akadmarccc on 2014-10-15
Hey guys,

Forgive me if i make newbie mistakes by not giving the right information off the bat. Basically I am attempting to share raid 1 mass storage (non-os purely storage drive) accross an ubuntu and windows installation - to acheive this I am trying to make use of my motherboards built in FakeRaid (Intel Matrix Storage Manager).

To make a long story short, I am enabling RAID in the regular BIOS setup, then entering the separate RAID bios setup and setting up Raid 1 on the two drives I want to use. From there I am using mdadm --assemble --scan, and then after resync formatting the drive in NFTS (I've also tried EXT4). 

The problem is that after the initial setup, resync and formatting everytime I restart the computer and reassemble the raid, the drives resync (every time). The only way that I've not seen a resync on reboot was when I intentionally didn't format after the initial mdadm setup and resync. If i don't format the disk, i can restart any number of times and re-assemble without issue. 

If anyone could give me any assistance or suggestions I would be grateful. 

Here are the details:

MDADM version: mdadm - v3.2.5 - 18th May 2012
Kernel: 3.13.0-34-generic
Ubuntu Version: 14.04

mdadm --detail-platform dump:

Platform : Intel(R) Matrix Storage Manager
version : 11.2.0.1527
RAID Levels : raid0 raid1 raid10 raid5
Chunk Sizes : 4k 8k 16k 32k 64k 128k
2TB volumes : supported
2TB disks : supported
Max Disks : 6
 Max Volumes : 2 per array, 4 per controller
I/O Controller : /sys/devices/pci0000:00/0000:00:1f.2 (SATA)

mdadm --examine /dev/sda dump (first disk being raid 1'd):

Magic : Intel Raid ISM Cfg Sig.
Version : 1.1.00
Orig Family : 416835bf
Family : 416835bf
Generation : 00000005
Attributes : All supported
UUID : eb428a9d:8159bbda:7efe6bcc:b81705a2
Checksum : fcc37e39 correct
MPB Sectors : 2
Disks : 2
RAID Devices : 1

Disk00 Serial : Z340LA5M
State : active
Id : 00000000
Usable Size : 3907023112 (1863.01 GiB 2000.40 GB)

[2tbr1]:
UUID : 8744828a:83f0f832:d7e1437d:5dd0bf03
RAID Level : 1 <-- 1
Members : 2 <-- 2
Slots : [UU] <-- [UU]
Failed disk : none
This Slot : 0
Array Size : 3907022848 (1863.01 GiB 2000.40 GB)
Per Dev Size : 3907023112 (1863.01 GiB 2000.40 GB)
Sector Offset : 0
Num Stripes : 15261808
Chunk Size : 64 KiB <-- 64 KiB
Reserved : 0
Migrate State : initialize
Map State : normal <-- uninitialized
Checkpoint : 462962 (512)
Dirty State : clean

Disk01 Serial : Z340LA1R
State : active
Id : 00000001
Usable Size : 3907023112 (1863.01 GiB 2000.40 GB)



mdadm --examine /dev/sdb dump (second disk being raid 1'd):

Magic : Intel Raid ISM Cfg Sig.
Version : 1.1.00
Orig Family : 416835bf
Family : 416835bf
Generation : 00000006
Attributes : All supported
UUID : eb428a9d:8159bbda:7efe6bcc:b81705a2
Checksum : fcc70aea correct
MPB Sectors : 2
Disks : 2
RAID Devices : 1

Disk01 Serial : Z340LA1R
State : active
Id : 00000001
Usable Size : 3907023112 (1863.01 GiB 2000.40 GB)

[2tbr1]:
UUID : 8744828a:83f0f832:d7e1437d:5dd0bf03
RAID Level : 1 <-- 1
Members : 2 <-- 2
Slots : [UU] <-- [UU]
Failed disk : none
This Slot : 1
Array Size : 3907022848 (1863.01 GiB 2000.40 GB)
Per Dev Size : 3907023112 (1863.01 GiB 2000.40 GB)
Sector Offset : 0
Num Stripes : 15261808
Chunk Size : 64 KiB <-- 64 KiB
Reserved : 0
Migrate State : initialize
Map State : normal <-- uninitialized
Checkpoint : 695586 (512)
Dirty State : clean

Disk00 Serial : Z340LA5M
State : active
Id : 00000000
Usable Size : 3907023112 (1863.01 GiB 2000.40 GB)

---

### Post by joe122 on 2014-10-15
I had a similar issue when I replaced both my RAID drives with new WD 2TB drives. Seems that in my case, the ISM software in my BIOS didn't support my new drives correctly. I found sites on the web that gave instructions on updating my BIOS with a newer version of the ISM software. I have an ASUS motherboard, and the newest ISM that was in a BIOS from ASUS was something like 7.6.6. Using the instructions I found on the web, I was able to update the ISM software to 11.6.0.1702, and now my drives work just fine in both Windows and Ubuntu (14.04LTS).

---

### Post by akadmarccc on 2014-10-15
Cool. Thanks for the TIP - I'll see about updating the IMSM. Just curious - when you were expeirencing the issue, did it work in Windows? Because I can get it to work in windows.

---

