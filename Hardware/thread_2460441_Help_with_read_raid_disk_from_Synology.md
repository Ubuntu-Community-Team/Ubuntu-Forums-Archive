---
title: "Help with read raid disk from Synology"
date: 2021-04-10
forum: Hardware
---

### Post by 2307pava on 2021-04-10
Please if osmebody can help me with read disk from Synology. My Synology was finish /  procesor / but I had in raid disk some data what I didnt backup. I try  with to recovery raid with mdadm -Asf && vgchange -ay ,  but can not open disk. Now in Ubuntu PC have one ssd disk 240 GB where is Ubuntu, and this raid disk form synology dev/md2
From testdrive have report:
Disk /dev/sda - 240 GB / 223 GiB - CHS 29185 255 63
Sector size:512
Model: KINGSTON SA400S37240G, S/N:50026B7380D84187, FW:S3700100

Disk /dev/sdb - 3000 GB / 2794 GiB - CHS 364801 255 63
Sector size:512
Model: WDC WD30EFRX-68EUZN0, S/N:WD-WCC4N1079199, FW:80.00A80

Disk /dev/md2 - 2995 GB / 2789 GiB - CHS 731361136 2 4
Sector size:512


Disk /dev/sda - 240 GB / 223 GiB - CHS 29185 255 63
     Partition            Start        End    Size in sectors
 1 * Linux                    0  32 33 29185  61 60  468858880
     ext4 blocksize=4096 Large_file Sparse_SB Recover

Disk /dev/sdb - 3000 GB / 2794 GiB - CHS 364801 255 63
     Partition            Start        End    Size in sectors
 1 P Linux Raid                  2048    4982527    4980480 [md0]
     md 0.90.0 B.Endian Raid 1: devices 0(8,1)* 1(8,17)
 2 P Linux Raid               4982528    9176831    4194304 [md1]
     md 0.90.0 B.Endian Raid 1: devices 0(8,2)* 1(8,18)
 3 P Linux Raid               9437184 5860328351 5850891168 [foodin:2]
     md 1.x L.Endian Raid 1 - Array Slot : 0 (0, failed, failed, failed, failed, failed, failed, failed, failed, failed, failed)

Disk /dev/md2 - 2995 GB / 2789 GiB - CHS 731361136 2 4
     Partition            Start        End    Size in sectors
   P btrfs                    0   0  1 731361135   1  4 5850889088 [2018.12.31-10:58:54 v23824]
     btrfs blocksize=4096

Sending also print screen. Please if can help me with this, I try all post on internet, also dont understand how is working raid...

Thank you so much

---

