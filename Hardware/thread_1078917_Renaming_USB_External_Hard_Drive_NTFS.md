---
title: "Renaming USB External Hard Drive NTFS"
date: 2009-02-23
forum: Hardware
---

### Post by captr24 on 2009-02-23
Hi All,

I have recently installed Ubuntu 8.10.  I have so far been able to mount two external NTFS drives.  Everything seems to work fine (i.e. read / write).  However, I am having issues renaming the drives.  I have followed the instructions found in the help files, however, am still unable to rename the drive and an error message pops up.

mars@mars-desktop:~$ sudo ntfslabel /dev/sde1 Lacie-sde1
Volume is scheduled for check.
Please boot into Windows TWICE, or use the 'force' option.
NOTE: If you had not scheduled check and last time accessed this volume
using ntfsmount and shutdown system properly, then init scripts in your
distribution are broken. Please report to your distribution developers
(NOT to us!) that init scripts kill ntfsmount or mount.ntfs-fuse during
shutdown instead of proper umount.

Any help is much appreciated.  Thanks.sudo

---

