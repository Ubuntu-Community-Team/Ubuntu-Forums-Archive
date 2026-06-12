---
title: "Ubuntu Cant see my RAID 1"
date: 2017-02-24
forum: Hardware
---

### Post by katana-9988 on 2017-02-24
Hi guys. I am using two 4TB drives as RAID 1 using the motherboard to have all my data. It is working will with CentOS, But I gess Ubuntu need some tweeking to do.

The information that I got:-

[IMG]https://i.stack.imgur.com/SE3Nc.jpg[/IMG]

ahmed@arkan:~$ dmesg | tail
[   14.955111] wlx5cd998c2f547: associated
[   14.955160] IPv6: ADDRCONF(NETDEV_CHANGE): wlx5cd998c2f547: link becomes ready
[   66.537356] EXT4-fs (dm-0): bad geometry: block count 976753920 exceeds size of device (439883041 blocks)
[  296.021304] EXT4-fs (dm-0): bad geometry: block count 976753920 exceeds size of device (439883041 blocks)
[  314.401983] EXT4-fs (dm-0): bad geometry: block count 976753920 exceeds size of device (439883041 blocks)
[  561.931592] EXT4-fs (dm-0): bad geometry: block count 976753920 exceeds size of device (439883041 blocks)
[  687.623557] systemd[1]: apt-daily.timer: Adding 7h 41min 2.586014s random time.
[  687.623739] systemd[1]: snapd.refresh.timer: Adding 4h 9min 42.826348s random time.
[  687.623745] systemd[1]: snapd.refresh.timer: Adding 3h 10min 18.720376s random time.
[  687.934658]  sdd: sdd1 < sdd5 >


The following is from gparted.

<i>Filesystem volume name:   Raid_Data
Last mounted on:          /mnt/f9a8ab95-9996-4978-a656-25c7fe243aa2
Filesystem UUID:          f9a8ab95-9996-4978-a656-25c7fe243aa2
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              244195328
Block count:              976753920
Reserved block count:     48837696
Free blocks:              684664036
Free inodes:              243846930
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      791
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Oct 11 17:56:22 2015
Last mount time:          Fri Feb 24 08:14:43 2017
Last write time:          Fri Feb 24 09:41:51 2017
Mount count:              398
Maximum mount count:      -1
Last checked:             Sun Mar  6 23:46:32 2016
Check interval:           0 (<none>)
Lifetime writes:          1474 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      d9a98f9a-d8d0-4e4a-9661-5db2d45f7c28
Journal backup:           inode blocks</i>

<i>dumpe2fs 1.42.13 (17-May-2015)
dumpe2fs: Invalid argument while reading journal super block</i>

<i>Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ext4 file system support:  e2fsprogs v1.41+.</i>

I check the Intel Raid Drivers and it is installed.

My guess is that I need to resize the raid 1 partition for it to work with Ubuntu. According to this post.[http://www.linuxquestions.org/questions/linux-general-1/cannot-mount-hard-disk-block-count-exceeds-size-of-device-bad-partition-table-880149/](http://www.linuxquestions.org/questions/linux-general-1/cannot-mount-hard-disk-block-count-exceeds-size-of-device-bad-partition-table-880149/)

Please advice me. I am afraid to do anything to the drive that will wipe out everything I got. 

So please give me the steps so I can read them and copy and past them.

Thanks,

---

### Post by ajgreeny on 2017-02-24
Duplicate at [https://ubuntuforums.org/showthread.php?t=2353697&p=13611971#post13611971](https://ubuntuforums.org/showthread.php?t=2353697&p=13611971#post13611971)
**Please do not create duplicate posts;** it is confusing for all including you and dilutes the forum's ability to help. 

Closed.

---

