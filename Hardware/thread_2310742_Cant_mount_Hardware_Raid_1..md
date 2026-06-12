---
title: "Cant mount Hardware Raid 1."
date: 2016-01-21
forum: Hardware
---

### Post by whitefish10 on 2016-01-21
Hello I am trying to mount my hardware Raid 1 partition but it gives an error whenever I am trying to do so. 

[http://postimg.org/image/6ybwnvr7p/](http://postimg.org/image/6ybwnvr7p/)

Note: I cant do anything to modify its partition since it has a lot of important data. Plus, it used to work well today on OpenSuse 42.1 and Fedora 23 on previews install before I moved to Ubuntu Gnome 15.10 today.
I believe that I am missing a package or something. That since Ubuntu Gnome cant identify the raid 1 partition. 

Please help me. And thank you.

---

### Post by whitefish10 on 2016-01-22
I got more info. I Installed gparted and this what I got.

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
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ext4 file system support:  e2fsprogs v1.41+.</i>

```


It seems that there is an issue with e2fsprogs.

Also, I did :-

```

ahmed@arkan:~$ dpkg -s e2fsprogs
Package: e2fsprogs
Essential: yes
Status: install ok installed
Priority: required
Section: admin
Installed-Size: 2961
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Version: 1.42.12-1ubuntu2
Replaces: hurd (<= 20040301-1), libblkid1 (<< 1.38+1.39-WIP-2005.12.10-2), libuuid1 (<< 1.38+1.39-WIP-2005.12.10-2)
Pre-Depends: e2fslibs (= 1.42.12-1ubuntu2), libblkid1 (>= 2.17.2), libc6 (>= 2.14), libcomerr2 (>= 1.42~WIP-2011-10-05-1), libss2 (>= 1.34-1), libuuid1 (>= 2.16), util-linux (>= 2.15~rc1-1)
Suggests: gpart, parted, e2fsck-static
Conflicts: dump (<< 0.4b4-4), initscripts (<< 2.85-4), quota (<< 1.55-8.1), sysvinit (<< 2.85-4)
Conffiles:
 /etc/mke2fs.conf e2cdbf0620e93949af5857eb4739f949
Description: ext2/ext3/ext4 file system utilities
 The ext2, ext3 and ext4 file systems are successors of the original ext
 ("extended") file system. They are the main file system types used for
 hard disks on Debian and other Linux systems.
 .
 This package contains programs for creating, checking, and maintaining
 ext2/3/4-based file systems.  It also includes the "badblocks" program,
 which can be used to scan for bad blocks on a disk or other storage device.
Homepage: http://e2fsprogs.sourceforge.net
Original-Maintainer: Theodore Y. Ts'o <tytso@mit.edu>


```

Ubuntu 15.10 is using version 1.42.12-1ubuntu2 (as per the website it is released on 29/8/2014) and the home page of e2fsprogs is having version 1.42.13 (17/5/2015). 

I am assuming that I could have a bug in the version I am using. 

Is there a way to work around this? Please advise me.

---

