---
title: "Cannot reform an external USB drive with Gparted"
date: 2009-06-27
forum: Hardware
---

### Post by learningcurb on 2009-06-27
I seem to be unable to reformat my external USB drive with Gparted for some reason.  I noticed that after the "set partition type" step, Nautilus would automatically mount the disk which would cause mkfs.ext3 to fail.  Any idea how I can stop the disk from being automatically mounted?

```
GParted 0.4.3

Libparted 1.8.8
Create Primary Partition #1 (ext3, 931.51 GiB) on /dev/sdb  00:00:21    ( ERROR )
     	
create empty partition  00:00:11    ( SUCCESS )
     	
path: /dev/sdb1
start: 63
end: 1953520064
size: 1953520002 (931.51 GiB)
set partition type on /dev/sdb1  00:00:10    ( SUCCESS )
     	
new partition type: ext3
create new ext3 file system  00:00:00    ( ERROR )
     	
mkfs.ext3 -L "" /dev/sdb1
     	
mke2fs 1.41.4 (27-Jan-2009)
/dev/sdb1 is mounted; will not make a filesystem here!

========================================
```

---

