---
title: "The different size between fdisk -l and df -h"
date: 2008-11-12
forum: General Help
---

### Post by jorge6422 on 2008-11-12
I used 2 seagate 250G hard disk for RAID 1 and created md8 as a new array which included sda9 and sdb9.
When I fdisk -l, it seems all right, md9 is 80GB, but when I df -h, md8 seems bacome 120G!
I can't solve this problem.... 

# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   fd  Linux raid autodetect
/dev/sda2             132        1437    10490445   fd  Linux raid autodetect
/dev/sda3            1438        2743    10490445   fd  Linux raid autodetect
/dev/sda4            2744       30401   222162885    5  Extended
/dev/sda5            2744        2875     1060258+  82  Linux swap / Solaris
/dev/sda6            2876        9376    52219251   fd  Linux raid autodetect
/dev/sda7            9377       13277    31334751   fd  Linux raid autodetect
/dev/sda8           13278       14588    10530576   fd  Linux raid autodetect
/dev/sda9           14589       24315    78132096   fd  Linux raid autodetect

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391   fd  Linux raid autodetect
/dev/sdb2             132        1437    10490445   fd  Linux raid autodetect
/dev/sdb3            1438        2743    10490445   fd  Linux raid autodetect
/dev/sdb4            2744       30401   222162885    5  Extended
/dev/sdb5            2744        2875     1060258+  82  Linux swap / Solaris
/dev/sdb6            2876        9376    52219251   fd  Linux raid autodetect
/dev/sdb7            9377       13277    31334751   fd  Linux raid autodetect
/dev/sdb8           13278       14588    10530576   fd  Linux raid autodetect
/dev/sdb9           14589       24315    78132096   fd  Linux raid autodetect

Disk /dev/md1: 10.7 GB, 10783227904 bytes
2 heads, 4 sectors/track, 2632624 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md4: 32.0 GB, 32086687744 bytes
2 heads, 4 sectors/track, 7833664 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md4 doesn't contain a valid partition table

Disk /dev/md3: 53.4 GB, 53472395264 bytes
2 heads, 4 sectors/track, 13054784 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md3 doesn't contain a valid partition table

Disk /dev/md6: 10.7 GB, 10742136832 bytes
2 heads, 4 sectors/track, 2622592 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md6 doesn't contain a valid partition table

Disk /dev/md2: 10.7 GB, 10742136832 bytes
2 heads, 4 sectors/track, 2622592 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md0: 106 MB, 106823680 bytes
2 heads, 4 sectors/track, 26080 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md8: 80.0 GB, 80007200768 bytes
2 heads, 4 sectors/track, 19533008 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md8 doesn't contain a valid partition table


# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              9.8G  1.2G  8.1G  13% /
/dev/md6              9.7G  211M  9.0G   3% /tmp
/dev/md4               29G  1.2G   27G   5% /var
/dev/md3               49G  3.2G   43G   7% /home
/dev/md2              9.7G  3.0G  6.3G  32% /usr
/dev/md0               99M   37M   57M  40% /boot
tmpfs                 1.4G     0  1.4G   0% /dev/shm
/dev/md8              120G  188M  113G   1% /photo

---

### Post by fjgaude on 2008-11-13
From what little I know, **fdisk** doesn't understand raid arrays, and the earlier versions of it gave bad readings. The latest verstion doesn't read the size of arrays at all.

I do believe that **df** shows what is correct.

---

### Post by jorge6422 on 2008-11-13
Thanks for your reply.
In the beginning, I trid to use **fdisk /dev/sda** and **fdisk /dev/sdb** to creat the 2 new partitons, sda9 and sdb9, the partitons were set as 80GB. After rebooting, I use **mdadm** to creat the new array-md8 which included sda9 and sdb9.
**fdisk -l** shows md8 was 80GB, I think it is correct. But when I df -h, md8 became 120GB. 
I fdisk the partition for 80GB. **fdisk -l** is correct. But **df -h** is wrong.

---

### Post by dcstar on 2008-11-13
> **jorge6422 said:**
> I used 2 seagate 250G hard disk for RAID 1 and created md8 as a new array which included sda9 and sdb9.
When I fdisk -l, it seems all right, md9 is 80GB, but when I df -h, md8 seems bacome 120G!
I can't solve this problem.... 
.......

fdisk show you **physical** partitions on storage devices, df shows you **logical** filesystems which can contain all sorts of things like links to other filesystems etc.

Only in specific circumstances will they ever be the same.

---

### Post by psusi on 2008-11-14
Are you sure you made a raid1 and not a raid0?  Did you format md9 after setting it up with dmraid, or is there some old trashed filesystem being picked up that used to be a larger partition?

---

### Post by jorge6422 on 2008-11-15
Finally, I've found the way to solve the problem.
I should **mkfs -t ext3 /dev/md8**.
Then the result of **df -h** would be correct.
Thanks for everybody...:guitar:

Here it is.....

# mdadm --creat /dev/md8 --level=1 --raid-devices=2 /dev/sd[ab]9
mdadm: /dev/sda9 appears to contain an ext2fs file system
    size=78132032K  mtime=Sat Nov 15 21:28:11 2008
mdadm: /dev/sda9 appears to be part of a raid array:
    level=raid1 devices=2 ctime=Fri Nov  7 14:48:41 2008
mdadm: /dev/sdb9 appears to contain an ext2fs file system
    size=78132032K  mtime=Sat Nov 15 21:28:11 2008
mdadm: /dev/sdb9 appears to be part of a raid array:
    level=raid1 devices=2 ctime=Fri Nov  7 14:48:41 2008
Continue creating array? yes
mdadm: array /dev/md8 started.
[root@sfs3 dev]# mdadm --detail /dev/md8
/dev/md8:
        Version : 00.90.03
  Creation Time : Sat Nov 15 21:54:25 2008
     Raid Level : raid1
     Array Size : 97667072 (93.14 GiB 100.01 GB)
    Device Size : 97667072 (93.14 GiB 100.01 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 8
    Persistence : Superblock is persistent

    Update Time : Sat Nov 15 21:54:25 2008
          State : clean, resyncing
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

 Rebuild Status : 1% complete

           UUID : 9336fdde:91d62c51:37533493:b516ba8f
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8        9        0      active sync   /dev/sda9
       1       8       25        1      active sync   /dev/sdb9
[root@sfs3 dev]# mkfs -t ext3 /dev/md8
mke2fs 1.39 (29-May-2006)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
12222464 inodes, 24416768 blocks
1220838 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
746 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 37 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
# mount /dev/md8 /photo
# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              9.8G  1.2G  8.1G  13% /
/dev/md6              9.7G  211M  9.0G   3% /tmp
/dev/md4               29G  1.2G   27G   5% /var
/dev/md3               49G  3.3G   43G   8% /home
/dev/md2              9.7G  3.0G  6.3G  32% /usr
/dev/md0               99M   37M   57M  40% /boot
tmpfs                 1.4G     0  1.4G   0% /dev/shm
/dev/md8               92G  188M   87G   1% /photo

# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   fd  Linux raid autodetect
/dev/sda2             132        1437    10490445   fd  Linux raid autodetect
/dev/sda3            1438        2743    10490445   fd  Linux raid autodetect
/dev/sda4            2744       30401   222162885    5  Extended
/dev/sda5            2744        2875     1060258+  82  Linux swap / Solaris
/dev/sda6            2876        9376    52219251   fd  Linux raid autodetect
/dev/sda7            9377       13277    31334751   fd  Linux raid autodetect
/dev/sda8           13278       14588    10530576   fd  Linux raid autodetect
/dev/sda9           14589       26747    97667136   fd  Linux raid autodetect

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391   fd  Linux raid autodetect
/dev/sdb2             132        1437    10490445   fd  Linux raid autodetect
/dev/sdb3            1438        2743    10490445   fd  Linux raid autodetect
/dev/sdb4            2744       30401   222162885    5  Extended
/dev/sdb5            2744        2875     1060258+  82  Linux swap / Solaris
/dev/sdb6            2876        9376    52219251   fd  Linux raid autodetect
/dev/sdb7            9377       13277    31334751   fd  Linux raid autodetect
/dev/sdb8           13278       14588    10530576   fd  Linux raid autodetect
/dev/sdb9           14589       26747    97667136   fd  Linux raid autodetect

Disk /dev/md1: 10.7 GB, 10783227904 bytes
2 heads, 4 sectors/track, 2632624 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md4: 32.0 GB, 32086687744 bytes
2 heads, 4 sectors/track, 7833664 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md4 doesn't contain a valid partition table

Disk /dev/md3: 53.4 GB, 53472395264 bytes
2 heads, 4 sectors/track, 13054784 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md3 doesn't contain a valid partition table

Disk /dev/md6: 10.7 GB, 10742136832 bytes
2 heads, 4 sectors/track, 2622592 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md6 doesn't contain a valid partition table

Disk /dev/md2: 10.7 GB, 10742136832 bytes
2 heads, 4 sectors/track, 2622592 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md0: 106 MB, 106823680 bytes
2 heads, 4 sectors/track, 26080 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md8: 100.0 GB, 100011081728 bytes
2 heads, 4 sectors/track, 24416768 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md8 doesn't contain a valid partition table

---

