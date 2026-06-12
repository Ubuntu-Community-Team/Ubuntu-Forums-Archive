---
title: "mount delays and blkid issue with 9.10"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Ian Goodacre on 2009-10-29
I installed 9.04 a few days ago - fresh install. Then I installed openerp-client and openerp-server. These installs completed successfully but the software wouldn't run. But a comment on one of the bug reports said that they recently installed and worked in Karmic, so I upgraded yesterday morning. Something went wrong towards the end of the upgrade (I didn't capture the error messages - I think it was trying to remove one of the packages related to openerp) but the upgrade proceeded.

After the upgrade my system works, but during boot I see the following:

fsck from util-linux-ng 2.16
one or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/...
/tmp: waiting for (null)
/boot: waiting for /dev/disk/by-uuid/...
/dev/sda6 clean...

(There were real UUIDs in the above, but I type too slowly to copy them).

Everything mounts successfully and the system runs fine, but I not also that /dev/.blkid.tab doesn't exist so /etc/blkid.tab is a broken link. If I run blkid then /dev/.blkid.tab is created. The UUIDs recorded are the same as those in /etc/fstab (/ and /boot are mounted by UUID).

So - system runs fine, but there is some slight delay accessing / and /boot by UUID during system initialization.

Is blkid relevant any more? I guess not, since my system runs without the cache being created.

Any idea why the file systems "cannot yet be mounted"?

---

### Post by Velophile on 2009-10-30
Sorry to cross post but it's pretty much as the same thing I noted here:

[http://ubuntuforums.org/showpost.php?p=8195848&postcount=31](http://ubuntuforums.org/showpost.php?p=8195848&postcount=31)

I'll have a look at the blkid stuff when I've got time over the weekend and see if mines similar to yours (broken link).

---

### Post by Velophile on 2009-10-30
Found this which might be relevant, I'll try moving those files and see if it stops the errors appearing and post results later:

[http://lists.debian.org/debian-user/2009/01/msg01877.html](http://lists.debian.org/debian-user/2009/01/msg01877.html)

---

### Post by Velophile on 2009-10-30
Didn't make any difference at all unfortunately so I changed /etc/fstab so it used devices rather than UUID's and found that it's the two LVM's the the boot sequence is waiting on.

---

