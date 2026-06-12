---
title: "How come Ubuntu won't install to software raid?"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by oshunluvr on 2009-10-15
I have setup and installed 4 other distros to software raid0 without and hitches. However, it seems this cannot be done with Ubuntu. How come?

Just to be clear: I'm not talking about bios setup "fake" raid or any raid controllers, just an mdadm device using raid0 for the root install.

/boot is not on the raid device so thats not it either.

It seems to me that hard drives are cheap and many if not most users have multiple drives. Raid0 is the cheapest and easiest way to gain drive access speed.

Just for the record here's the procedure that works for other distros:

1. Boot liveCD
2. Install mdadm
3. Assemble arrays
4. Install OS to /boot (not in RAID) partition and to / (RAID0) partition
5. Reboot and good to go.

This method does not work with kubuntu jaunty. The steps above resulted in boot error "device /dev/md0 does not exist". I guessed mdadm and raid were not enabled by default nor enabled in initramfs. So I did a side-by install to a non-RAID partition, installed mdadm, rebuilt initrd with mdadm and raid0,1,5 enabled and then manually copied mdadm files from install to RAID partition and rebooted to RAID. This resulted in a similar error at boot time, but when dumped to the command line (busybox or initramfs command line or whatever you guys call it) the error still said /dev/md0 did not exist, but a quick "cat /proc/mdstat" showed all my RAID partitions up and running.

What can I do to fix this?

---

### Post by i.r.id10t on 2009-10-15
I think that either the alternative or server cd will allow installing to software raid

---

### Post by oshunluvr on 2009-10-15
Thanks dude (or dudette whichever... :) ) - that was easy.

A few other things seem different (i.e. better) from the livecd installer too.

Desktop comes up much faster now thanks again!

---

