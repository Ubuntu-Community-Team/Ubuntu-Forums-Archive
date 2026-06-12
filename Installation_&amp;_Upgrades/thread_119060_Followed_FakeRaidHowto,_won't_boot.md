---
title: "Followed FakeRaidHowto, won't boot"
date: 2006-01-18
forum: Installation &amp; Upgrades
---

### Post by jshellman on 2006-01-18
I followed the [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) and everything went fine until I booted it up after all done.

I got the following errors and then was dropped into busybox.

[131.119319] ehci_hcd 000:00:02.1: BIOS handoff failed (160,1010001)
mdadm: /dev/md0 has been started with 1 drive (out of 2)
mdadm: /dev/md1 assembled from 1 drive - not enough to start the array
mdadm: /dev/md1 assembled from 1 drive - not enough to start the array
  /dev/cdrom: open failed:no medium found
  unable to find volume group "nvidia_acbcdcbc5"
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init

Any ideas?

Thanks!

---

