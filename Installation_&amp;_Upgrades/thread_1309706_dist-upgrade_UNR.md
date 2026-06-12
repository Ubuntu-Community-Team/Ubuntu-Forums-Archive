---
title: "dist-upgrade UNR"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by bjlockie on 2009-11-01
I changed my fstab from tmpfs and it boots but is asking me for the password to log in.
I have no clue what it is, it was all automatic before.
I booted a system rescue USB and changed the root password but I forgot to change the user password.

Grr, third USB boot is the charm.
I forgot to change home for my user to a local disk, not the mmcblck one (which won't mount).

I use an Acer Aspire One netbook.
The system updater said there was a new distribution so I did that.
It updated to the 9.10 UNR release, right?

I can't even boot now. :-(
It starts to boot and then loops:
Filesystem checks are in progress
OR goes right to:One or more of the mounts listed in /etc/fstab cannot yet be mounted:
/home: waiting for /dev/mmcblk0p1
/var/log/apt: waiting for tmpfs
/var/log: waiting for tmpfs
/var/tmp: waiting for tmpfs

I press ESC to get a recovery shell:
# mount
/dev/sda1 on /
proc on /proc
none on /sys
none on /sys/fs/fuse/connections
none on /sys/kernel/security
udev on /dev
none on /dev/pts
none on /dev/shm
tpfs on /tmp
none on /var/run
none on /var/lock
none on /lib/init/rw

---

