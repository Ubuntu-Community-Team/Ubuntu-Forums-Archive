---
title: "Strange USB pendrive behaviour"
date: 2008-09-18
forum: Hardware
---

### Post by jtappin on 2008-09-18
I have a SanDisk Cruzer 4Gb pendrive, which behaves in a rather odd way.

Normally (maybe 8 times out of 10) it just mounts normally as a removable usb volume, but occasionally it also mounts part of the volume as a CD-ROM, in that case only the CD-ROM icon appears on the KDE desktop and unmounting (ejecting) it doesn't unmount the main part (unlike for removable HDDs with multiple partitions). As far as I can see from the syslog, there is always a "CD-ROM" detected but only occasionally does the system try to mount it.

FWIW: on a Windows box or a Solaris box the CDROM bit always mounts separately.

Is there anything to do other than reformat the stick?

---

### Post by timcredible on 2008-09-18
the extra cd-rom thing is the u3 partition on the drive - it holds encryption software for windows so you can encrypt your data on the drive if you're using windows.  you can just delete that partition with gparted if you want.  or reformat it to ext3, or fat16, or fat32, whatever you prefer, but the main partition doesn't need to have anything done to it.

---

