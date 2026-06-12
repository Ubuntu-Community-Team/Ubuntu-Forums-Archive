---
title: "Restoring a degraded RAID 1 array partition."
date: 2009-09-21
forum: Hardware
---

### Post by Crafty Kisses on 2009-09-21
The issue that I'm having is with RAID is that one of my partitions appear to be degraded. Here is my current filesystem:
```
Filesystem            Size  Used Avail Use% Mounted on 
/dev/md1              146G  9.4G  131G   7% / 
/dev/md0               98M   31M   63M  34% /boot 
/dev/hda1             265G   12G  240G   5% /
```
Now I noticed that if I try to add hda1 back to mda1 by running:
```
mdadm /dev/md1 -a /dev/hda1
```
I get an argument error, here is the exact error:
```
mdadm: hot add failed for /dev/hda1: Invalid argument
```
So then I thought, maybe I should remove the partition then try re-adding hda1, so I ran:
```
mdadm /dev/md1 -r /dev/hda1-a /dev/hda1
``` 
Then I get another error, which is:
```
mdadm: hot remove failed for /dev/hda1: No such device or address
```
Now I could try forcing this by running:
```
mdadm -v --assemble --run --force /dev/md1 /dev/hdb2 /dev/hda1
```
I just don't want to risk data being lost, so I'm kind of in a tricky situation here, any thoughts?

---

