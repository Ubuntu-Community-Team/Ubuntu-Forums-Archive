---
title: "Problems Mounting Drives After Installing Ubuntu 9.10"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by jameshogan on 2009-11-07
Hi All,

Ok, this issue's been bugging me for the last 2 days, since my install of Ubuntu 9.10 yesterday.  It looks like 9.10 has altered my /etc/fstab file and now I'm having difficulty mounting my drivers.  Needless to say, I'm in tears.

*sob*

Ok, here's the output of a blkid to establish which filesystems are around the place:

root@Adam:~# blkid
/dev/sda1: UUID="b676529e-4918-4ad7-8602-431aa0121fd7" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: UUID="a1dbfe4a-c963-413d-96ac-a42d0d8202b4" TYPE="swap"
/dev/sdb1: LABEL="BackUp" UUID="4a778504-b768-4947-b22f-3bd37f617be8" SEC_TYPE=ext2" type="ext3"


From there, I've re-written my /etc/fstab to be:

# /etc/fstab: static file system information.
#
# <file system>   <mount point>  <type>  <options>  <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=b676529e-4918-4ad7-8602-431aa0121fd7 / ext3 relatime,errors=remount-ro,defaults 0 1
# /dev/sda5
UUID=a1dbfe4a-c963-413d-96ac-a42d0d8202b4 none swap sw 0 0


but, on a reboot, I get:

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/b676529e-4918-4ad7-8602-431aa0121fd7
/tmp: waiting for (null)
swap: waiting for UUID=a1dbfe4a-c963-413d-96ac-a42d0d8202b4

after paying a lot of attention that all the UUID characters & digits line up, I'm at a loss as to why my system doesn't sing.

Any ideas world?


Best regards,
James

---

### Post by jameshogan on 2009-11-07
Ooo oooo oooo ooo !  Searching the forum, I've found this:
[http://ubuntuforums.org/showthread.php?t=1297318&highlight=mounts+listed+%2Fetc%2Ffstab+mounted&page=2](http://ubuntuforums.org/showthread.php?t=1297318&highlight=mounts+listed+%2Fetc%2Ffstab+mounted&page=2)

and I'm dying to check it out.

Problem MIGHT be fixed....

---

