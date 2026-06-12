---
title: "mdadm not seeing full disk size"
date: 2017-07-14
forum: Hardware
---

### Post by hbj on 2017-07-14
I am running Ubuntu 16.04 with a software RAID1 which had 2 x 2TB drives, and I replaced it with 2 X 6TB drives by failing and replacing each drive in turn.  Basic procedure:

```
sudo mdadm --manage /dev/md4 --fail /dev/sdb1
sudo mdadm --manage /dev/md4 --remove /dev/sdb1

```
(swap drives, partition new drive)```

sudo mdadm --manage /dev/md4 --add /dev/sdb1
```
I got the following warning:
```
mdadm: /dev/sdb1 is larger than /dev/md4 can effectively use.
      Add --force is you really want to add this device.
```
so I added --force.  Then after recovery completes, I do the same with the second drive.  Then:
```
sudo mdadm --assemble /dev/md4 --update=devicesize
sudo mdadm --grow /dev/md4 --bitmap none
sudo mdadm --grow /dev/md4 --size max
sudo resize2fs -p /dev/md4
```
This all worked fine, EXCEPT that mdadm only grew to 4TB instead of to 6TB.  Disk utilities like parted (gparted) or gnome-disks show my two 6TB drives, and lsblk also recognizes the two 6TB drives:
```
[FONT=Courier New]> sudo lsblk                                                                                           
NAME    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT                                                                        
sdb       8:16   0   5.5T  0 disk                                                                                    
&#9492;&#9472;sdb1    8:17   0   5.5T  0 part                                                                                    
  &#9492;&#9472;md4   9:4    0     4T  0 raid1 /export/home                                                                      
sdd       8:48   0   5.5T  0 disk                                                                                    
&#9492;&#9472;sdd1    8:49   0   5.5T  0 part                                                                                    
  &#9492;&#9472;md4   9:4    0     4T  0 raid1 /export/home      [/FONT]
```
The system recogizes the 2 x 6TB drives but mdadm only grew from 2TB to 4TB (instead of 6TB) and says it has reached the maximum size:
```

> sudo mdadm --grow /dev/md4 --size max                                                                
mdadm: component size of /dev/md4 unchanged at 4294967295K          
                                                 
> sudo resize2fs -p /dev/md4                                                                           
resize2fs 1.42.13 (17-May-2015)                                                                                      
The filesystem is already 1073741823 (4k) blocks long.  Nothing to do!                                               

```
Any idea what might be causing mdadm to think it can only grow to 4TB instead of to the full 6TB available?

---

