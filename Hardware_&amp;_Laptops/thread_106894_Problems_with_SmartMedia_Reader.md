---
title: "Problems with SmartMedia Reader"
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by Poncho on 2005-12-21
Hello all:

I am having trouble getting my PQI 5-in-1 travel flash reader to work with Ubuntu 5.10.  When I plug the device in Ubuntu detects it but when I try to mount / acess the reader I get the following message:

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Error: could not execute pmount

dmesg give the following:

[4296527.244000] VFS: Can't find ext3 filesystem on dev sda.
[4296527.266000] VFS: Can't find ext3 filesystem on dev sda.
[4296527.288000] VFS: Can't find an ext2 filesystem on dev sda.
[4296527.309000] VFS: Can't find an ext2 filesystem on dev sda.
[4296527.361000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4296527.413000] ReiserFS: sda: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda
[4296527.447000] XFS: bad magic number
[4296527.447000] XFS: SB validate failed
[4296527.481000] XFS: bad magic number
[4296527.481000] XFS: SB validate failed

Any ideas on what I can do?

Thanks

---

