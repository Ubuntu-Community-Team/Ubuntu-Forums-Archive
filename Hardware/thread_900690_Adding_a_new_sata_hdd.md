---
title: "Adding a new sata hdd"
date: 2008-08-25
forum: Hardware
---

### Post by netpumber on 2008-08-25
Hey out there !!! I have bought a new sata hdd 500GB. The hdd tha the ubuntu are stored in is ide 80GB. Now when i have connect the sata the system doesn't recognize it. I run the gparted and nothing again... 
this is my /etc/fstab file 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ac20594b-6514-4d25-938d-86cec193bd75 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=5f204d79-72e0-4b4e-9d5e-4a24436edf0f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0 

```


and this is the output of the 
```

dmesg | grep sd
``` command :

```
[  135.384766] Driver 'sd' needs updating - please use bus_type methods
[  135.384857] sd 4:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[  135.384870] sd 4:0:0:0: [sda] Write Protect is off
[  135.384872] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  135.384886] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  135.384932] sd 4:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[  135.384940] sd 4:0:0:0: [sda] Write Protect is off
[  135.384942] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  135.384954] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  135.384958]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[  135.394416]  sda1 sda2
[  135.420513] sd 4:0:0:0: [sda] Attached SCSI disk
[  135.426389] sd 4:0:0:0: Attached scsi generic sg0 type 0
[  152.402801] Adding 5984204k swap on /dev/sda2.  Priority:-1 extents:1 across:5984204k
[  152.935721] EXT3 FS on sda1, internal journal
[  157.561640] audit(1219669408.311:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=8521 profile="/usr/sbin/cupsd" namespace="default"
```

What you say ? how i can make the system recognize it ? Thanx in advance!! :)

---

### Post by silkstone on 2008-08-25
If it's a brand new drive, it may not be formatted. Does gparted not see the drive at all - if you click the box near the top-right to show other drives?

---

### Post by netpumber on 2008-08-25
oh yea gparted doesn'e see the drive at all!! :(

---

### Post by netpumber on 2008-08-26
So ... does anyone have an idea?

---

### Post by netpumber on 2008-08-26
if i put the sata hdd in a windows system and format it from there in ext3 mabe it get work...

---

