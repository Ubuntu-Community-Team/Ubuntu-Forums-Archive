---
title: "SATA RAID Drives Detected Too Late"
date: 2005-02-14
forum: Hardware &amp; Laptops
---

### Post by daver on 2005-02-14
I am trying to get my software SATA RAID's (RAID1) to mount at boot time as /home and /opt as they did on my previous RHEL 3 system.  I have tried everything I can think of to get them loaded - I have a working mdadm.conf, both md0 and md1 can be mounted after logging on, and the RAIDs are healthy.  Ubuntu is not loading the modules needed to access SATA drives until well after is has done all its disk and RAID drive mounting.   I put all the necessary modules into /etc/modules:


# /etc/modules: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line.  Comments begin with
# a "#", and everything on the line after them are ignored.
libata
sd_mod
sr_mod
sbp2
scsi_mod
md
raid1
psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp

This is my mdam.conf:

DEVICE /dev/sda*
DEVICE /dev/sdb*
ARRAY /dev/md0 devices=/dev/sda1,/dev/sdb1
ARRAY /dev/md1 devices=/dev/sda2,/dev/sdb2


The error I get is a "No devices found" message at boot time when /etc/rcS.d/S25mdadm-raid is called.   That message doesn't seem to find its way into /var/log/messages or /var/log/syslog so I can't quote it here.   I have been able to determine that the devices it is talking about are the SATA drives.  I have ensured that the device nodes are being created and are present during boot, and I fixed a minor bug inS25mdadm-raid that failed to use the /etc/mdadm.conf file  The SATA drives aren't present when the RAID tries to load.  It loads fine after I logon, but by then it is too late to remap the /home directories.

What have I missed?

---

