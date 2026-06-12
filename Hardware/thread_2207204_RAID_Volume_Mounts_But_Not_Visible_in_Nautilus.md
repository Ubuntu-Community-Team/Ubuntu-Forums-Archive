---
title: "RAID Volume Mounts But Not Visible in Nautilus"
date: 2014-02-22
forum: Hardware
---

### Post by mulluysavage on 2014-02-22
df -h /media returns

/dev/md3 mounted on /media

does not show on Nautilus in Devices tab, or within  /media

---

### Post by mulluysavage on 2014-02-22
mdadm.conf

> # mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=6be0cade:9c410962:f0f2012d:698e4d9d name=philcloud:0
ARRAY /dev/md/1 metadata=1.2 UUID=8fdab9b9:3836af06:3654dfca:434a307d name=philcloud:1
ARRAY /dev/md/2 metadata=1.2 UUID=e1c1aa13:d65a4bd4:4797fed7:93654f19 name=philcloud:2
ARRAY /dev/md/3 metadata=1.2 UUID=9ba3c48e:ba4991b3:18b182e7:59ab1d30 name=philcloud:3

# This file was auto-generated on Sat, 22 Feb 2014 10:30:25 -0500
# by mkconf $Id$

---

### Post by mulluysavage on 2014-02-22
/etc/fstab

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md1 during installation
UUID=20a7c249-f5e5-4e8f-b4c5-e425d5ad8394 /               ext4    errors=remount-ro 0       1
# swap was on /dev/md0 during installation
#UUID=86759ee4-c529-4665-80f7-5e5ecfb534d9 none            swap    sw              0       0
#UUID=86759ee4-c529-4665-80f7-5e5ecfb534d9 /dev/sda5 swap sw 0 0
philcloud:0 /dev/sda5 swap sw 0 0
#UUID=37776d3e-f1c1-4e54-befb-1595ab8ff3e0 Cloud Storage Volume on /dev/md3
#LABEL=PhilCloudStorage philcloud:3 /media ext4 defaults
#LABEL=PhilCloudStorage /dev/md/3 /media ext4 defaults
UUID=9ba3c48e-ba4991b3-18b182e7-59ab1d30 /media ext4 defaults

---

