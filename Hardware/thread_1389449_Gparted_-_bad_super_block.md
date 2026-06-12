---
title: "Gparted - bad super block"
date: 2010-01-24
forum: Hardware
---

### Post by wyomingpat on 2010-01-24
My hard disk has a separate partition for the /home. I shrank the system partition - that was OK. Then resized the the home partition. It is not now accessible and fails to mount with any of the disk utilities although they can see the disk OK. Disk utility sees it fine and reports it as Linux 0x83

Gparted reports:
GParted 0.5.0
 Libparted 1.8.8.git-dirty
    **Grow /dev/sda5 from 184.91 GiB to 193.75 GiB**  00:00:00    ( ERROR )             calibrate /dev/sda5  00:00:00    ( SUCCESS )             [I]path: /dev/sda5
start: 61432623
end: 449209529
size: 387776907 (184.91 GiB)[/I]          check file system on /dev/sda5 for errors and (if possible) fix them  00:00:00    ( ERROR )             ***e2fsck -f -y -v /dev/sda5***             [I]e2fsck: Group descriptors look bad... trying backup blocks...
e2fsck: going back to original superblock
Filesystem mounted or opened exclusively by another program?
[/I]       [I]e2fsck 1.41.9 (22-Aug-2009)
e2fsck: The ext2 superblock is corrupt when using the backup blocks 
e2fsck: Device or resource busy while trying to open /dev/sda5 
[/I]             ========================================


Paragon says it is an ext2fs system. Mount manager sees it fine but it will not mount.
Syslog reports:
Jan 24 11:01:20 patd-laptop kernel: [ 2298.219181] EXT4-fs (sda5): ext4_check_descriptors: Checksum for group 0 failed (25801!=0)
Jan 24 11:01:20 patd-laptop kernel: [ 2298.219190] EXT4-fs (sda5): group descriptors corrupted!

---

### Post by ibuclaw on 2010-01-24
> **wyomingpat said:**
> My hard disk has a separate partition for the /home. I shrank the system partition - that was OK. Then resized the the home partition. It is not now accessible and fails to mount with any of the disk utilities although they can see the disk OK. Disk utility sees it fine and reports it as Linux 0x83

Gparted reports:
GParted 0.5.0
 Libparted 1.8.8.git-dirty
    **Grow /dev/sda5 from 184.91 GiB to 193.75 GiB**  00:00:00    ( ERROR )             calibrate /dev/sda5  00:00:00    ( SUCCESS )             [I]path: /dev/sda5
start: 61432623
end: 449209529
size: 387776907 (184.91 GiB)[/I]          check file system on /dev/sda5 for errors and (if possible) fix them  00:00:00    ( ERROR )             ***e2fsck -f -y -v /dev/sda5***             [I]e2fsck: Group descriptors look bad... trying backup blocks...
e2fsck: going back to original superblock
Filesystem mounted or opened exclusively by another program?
[/I]       [I]e2fsck 1.41.9 (22-Aug-2009)
e2fsck: The ext2 superblock is corrupt when using the backup blocks 
e2fsck: Device or resource busy while trying to open /dev/sda5 
[/I]             ========================================


Paragon says it is an ext2fs system. Mount manager sees it fine but it will not mount.
Syslog reports:
Jan 24 11:01:20 patd-laptop kernel: [ 2298.219181] EXT4-fs (sda5): ext4_check_descriptors: Checksum for group 0 failed (25801!=0)
Jan 24 11:01:20 patd-laptop kernel: [ 2298.219190] EXT4-fs (sda5): group descriptors corrupted!

Have you tried rebooting to ensure that no process is using /dev/sda5 ?

Leave the LiveCD in your machine so that your system boots up from the cdrom again, and then retry the fsck on the filesystem.

Regards
Iain

---

### Post by wyomingpat on 2010-01-24
Yes rebooted to the 9.10 system disk. Changed the FSTAB file so I can boot in on the system partion and that is all OK. Can see the disk with all utitities but cannot mount - still get the bad superblock message. Tried a repair with fsck but that was not successful.

---

### Post by ibuclaw on 2010-01-24
So what is the output of:
```
sudo e2fsck -f -y -v /dev/sda5
```
When ran in a terminal on the LiveCD?

And when you try to mount it:
```
sudo mount /dev/sda5 /mnt
```
What is outputted into the terminal?

And what gets returned when you run:
```
dmesg | tail -n15
```
After doing the above?

Regards
Iain

---

### Post by wyomingpat on 2010-01-24
Hi Iain I appreciate the help - I did work on Unix many moons ago but had a sleep since then!
anyhow....

3924930 13924931 13924932 13924933 13924934 13924935 13924936 13924937 13924938 13924939 13924940 13924941 13924942 13924943 13924944 13924945 13924946 13924947 13924948 13924949 13924950 13924951 13924952 13924953 13924954 13924955 13924956 13924957 13924958 13924959 13924960 13924961 13924962 13924963 13924964 13924965 13924966 13924967 13924968 13924969 13924970 13924971 13924972 13924973 13924974 13924975 13924976 13924977 13924978 13924979 13924980 13924981 13924982 13924983 13924984 13924985 13924986 13924987 13924988 13924989 13924990 13924991 13924992 13924993 13924994 13924995 13924996 13924997 13924998 13924999 13925000 13925001 13925002 13925003 13925004 13925005 13925006 13925007 13925008 13925009 13925010 13925011 13925012 13925013 13925014 13925015 13925016 13925017 13925018 13925019 13925020 13925021 13925022 13925023 13925024 13925025 13925026 13925027 13925028 13925029 13925030 13925031 13925032 13925033 13925034e2fsck: Can't allocate inode element

e2fsck: aborted
root@patd-laptop:~# 
root@patd-laptop:~# 
root@patd-laptop:~# 
root@patd-laptop:~# ^C
root@patd-laptop:~# sudo mount /dev/sda5 /mnt
mount: Stale NFS file handle
root@patd-laptop:~# ^C
root@patd-laptop:~# dmesg | tail -n15
[ 2361.508216] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
[ 2481.513022] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
[ 2601.512909] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
[ 2721.512727] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
[ 2841.513561] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
[ 2961.513286] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 382
[ 3081.513629] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
[ 3201.510615] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
[ 3321.513394] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
[ 3441.512780] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
[ 3561.510502] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
[ 3681.513353] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
[ 3730.451999] EXT4-fs (sda5): get root inode failed
[ 3730.452036] EXT4-fs (sda5): mount failed
[ 3801.509597] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 279
root@patd-laptop:~# 

Partition Manager 2009 booted off CD thinks it is an EXT2 and Gparted thinks it is an EXT4 which is what it should be.

---

### Post by ibuclaw on 2010-01-25
Hmm, ext4 partition... you didn't try resizing it, did you?

edit: 
> **wyomingpat said:**
> My hard disk has a separate partition for the /home. I shrank the system partition - that was OK. Then resized the the home partition.
I seemed to have missed that small detail, d'oh.

---

### Post by ibuclaw on 2010-01-25
OK, you could probably try:
```
sudo resize2fs /dev/sda5
```
To see if that might fix the problem.

But what you may need to do is resize the partition back to it's normal size again in fdisk.
Which will be a bummer trying to explain if you don't know your way through. ;)

Regards
Iain

---

