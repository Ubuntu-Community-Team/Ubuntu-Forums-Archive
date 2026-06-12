---
title: "How to upgrade e2fsprogs 1.42.12 to version 1.42.13"
date: 2016-01-22
forum: Hardware
---

### Post by whitefish10 on 2016-01-22
Hello, I have a hardware raid 1 configured on my motherboard. And according to the following I need to update e2fsprogs for it to work.

The following is from gparted.

```

<i>Filesystem volume name:   Raid_Data
Last mounted on:          /mnt/Raid_Data
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
Free blocks:              812409836
Free inodes:              244004368
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
Last mount time:          Thu Jan 21 16:08:59 2016
Last write time:          Thu Jan 21 16:24:29 2016
Mount count:              84
Maximum mount count:      -1
Last checked:             Thu Nov 12 00:28:45 2015
Check interval:           0 (<none>)
Lifetime writes:          699 GB
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

<i>dumpe2fs 1.42.12 (29-Aug-2014)
dumpe2fs: Invalid argument while reading journal super block</i>

<i>Unable to read the contents of this file system!
[U][B]Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ext4 file system support:  e2fsprogs v1.41+[/B][/U].</i>

```

I got to the e2fsprogs website and I got the package from source to compile. Just asking if there are any issues behind me doing so? And how can I do this? can I just install the new package and it will update what I have or remove first?

Note: I am sure that the raid 1 partition is working well. Before I install Ubuntu gnome 15.10 yesterday, I was using OpenSuse 42.1 with no issues and it is the same before that with Fedora 23. And I can't create a new partition on it since it has lots of important data.

Please advise me. Since I am out of options and if this don't work I will be force to change distribution :(.

Thanks,

---

