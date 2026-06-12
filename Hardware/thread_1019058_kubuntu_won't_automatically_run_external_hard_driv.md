---
title: "kubuntu won't automatically run external hard drive"
date: 2008-12-22
forum: Hardware
---

### Post by Macseaforth on 2008-12-22
Hi

I am using kubuntu 8.10. I keep most of my music, video etc on an external hard drive which is pretty much always plugged in. I would like to keep an icon in the panel for it for quick access, so I put one there, but it disappears every time I shut down the computer. Likewise, when I set amarok to populate the playlist from this drive it works fine, but when I shut down/restart it doesn't find the path automatically and I have to click on the drive in Kmenu>Computer for amarok to notice it.

I used ubuntu 8.10 for a few weeks and it recognised the drive and found set paths without any problems.

I'm sure there is a very simple command to fix this minor inconvenience, but I can't work it out. Little help?

---

### Post by taurus on 2008-12-22
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Macseaforth on 2008-12-23
"sudo fdisk -l" outputs:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14918   119828803+  83  Linux
/dev/sda2           14919       30401   124367197+   5  Extended
/dev/sda5           29836       30401     4546363+  82  Linux swap / Solaris
/dev/sda6           14919       29269   115274344+  83  Linux
/dev/sda7           29270       29835     4546363+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8004 MB, 8004132864 bytes
255 heads, 63 sectors/track, 973 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a410a40

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         973     7815591    b  W95 FAT32

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacdd9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77825   625129281    c  W95 FAT32 (LBA)

"sudo blkid" outputs:

/dev/sda1: UUID="ca81cfd2-be8e-484d-af37-c17b3a2e945a" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="56100765-8109-4535-ad9a-adf6560c21eb"
/dev/sda6: UUID="3963da1f-7eb8-4c49-9ae9-3b2b99ca8171" TYPE="ext3"
/dev/sda7: TYPE="swap" UUID="59e6a025-09c0-41e5-b1da-7d78aa94ac64"
/dev/sdb1: UUID="0C71-36A4" TYPE="vfat"
/dev/sdc1: LABEL="Elements" UUID="26A9-A5A9" TYPE="vfat"

"cat /etc/fstab" outputs:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=3963da1f-7eb8-4c49-9ae9-3b2b99ca8171 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=59e6a025-09c0-41e5-b1da-7d78aa94ac64 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

"df -h" outputs:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             109G   22G   82G  21% /
tmpfs                 759M     0  759M   0% /lib/init/rw
varrun                759M  100K  759M   1% /var/run
varlock               759M     0  759M   0% /var/lock
udev                  759M  2.8M  756M   1% /dev
tmpfs                 759M     0  759M   0% /dev/shm
lrm                   759M  2.0M  757M   1% /lib/modules/2.6.27-9-generic/volatile

---

