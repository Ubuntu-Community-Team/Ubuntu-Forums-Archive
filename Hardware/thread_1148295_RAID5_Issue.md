---
title: "RAID5 Issue"
date: 2009-05-04
forum: Hardware
---

### Post by P1ank on 2009-05-04
Hi guys, I've got a little problem

I recently had a massive failure of my old Windows install and decided to move over to something that works the way it's supposed to.

I have a nVidia RAID running in RAID 5, which was my data storage area and it's full of all my old data, so I don't want to do anything to descructive just yet. I've already done some reading and research and have already installed dmraid, I can see the what I'm supposed to in /dev/mapper but when I run dmraid -tay I see:

nvidia_bbedefhf: 0 1953546240 raid45 core 2 131072 nosync raid5_ls 1 128 3 -1208771632 /dev/sdc 0 /dev/sdd 0 /dev/sdb 0
ERROR: dos: reading /dev/mapper/nvidia_bbedefhf[No such file or directory]

Now as far as I've read that error should not happen. Not really to sure what else to say, the drive are available at sdb sdc ans sdd. I also an fdisk -l and these are the results

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf070f070

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5695a65

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4656e925

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976768033+  42  SFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb33fb340

   Device Boot      Start         End      Blocks   Id  System


Any help would be great

Thanks

---

