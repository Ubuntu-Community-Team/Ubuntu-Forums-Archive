---
title: "NTFS-3G issues"
date: 2013-09-27
forum: Hardware
---

### Post by dewdude on 2013-09-27
Hi,

I'm about to run myself up a wall with this.

I'm running ubuntu 12.04 on a laptop; it currently has an external USB drive connected formatted for NTFS. The standard install seems to work fine; except every 24 hours the system unmounts the drive for no reason; despite having a cronjob to touch a file every 3 minutes to prevent the drive from timing out. The obvious solution of reformatting to ext3 will not work; I do not have a drive large enough to back it up on for this purpose and I need to maintain compatibility with windows.

I've looked around and it's a bug in the version of ntfs-3g in 12.04. I tried compiling the recent version; but I can't get Ubuntu to want to use it. I've tried specifying it's mount in /etc/fstab for ntfs-3g; but all I get are permissions errors. I get the permissions fixed; and I get stuff about "drive is busy" or "already mounted". When FUSE does finally mount; it's mounted ro with "ntfs".

I'd like to use my own compiled version; but I'm missing something. I found a few things on this forum referring to older versions of Ubuntu ([http://ubuntuforums.org/showthread.php?t=1661757](http://ubuntuforums.org/showthread.php?t=1661757)), and I've done everything I thought I could to make it work...but it's been so long since I've had to do this I'm lost.

Can someone point me in the right direction on how to fix this issue?

---

