---
title: "mdadm RAID0 configuration pretty slow..."
date: 2010-12-28
forum: Hardware
---

### Post by ownaginatious on 2010-12-28
So I have two 1.5 TB drives in RAID0 configuration, and the RAID is approximately 28% full. I'm using mdadm to build the RAID, and right now I'm getting speeds of approximately 12 MB/s max when copying from an internal hard-drive to the RAID.

Now this seems ridiculously slow... and ideas what could be causing it?

Here is my mdadm configuration, if it matters:
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 super-minor=0
ARRAY /dev/md1 super-minor=1

# This file was auto-generated on Sun, 02 May 2010 17:00:23 -0400
# by mkconf 3.0.3-2

```

---

### Post by Fafler on 2010-12-28
```
cat /proc/mdstat
```

What drives and controllers do you use?

---

