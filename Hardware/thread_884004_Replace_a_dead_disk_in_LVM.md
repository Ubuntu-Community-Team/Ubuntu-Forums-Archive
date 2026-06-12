---
title: "Replace a dead disk in LVM"
date: 2008-08-08
forum: Hardware
---

### Post by dscheste on 2008-08-08
Hello,
I have four drives in a system where sda is a system and home drive, the other three build an LVM for /media.

One of the drives died. 

How can I replace it?

I was lucky enough to boot up once with the drive being recognized, so I immediately ran to a store, got myself an identical drive and did dd if=deaddrive of=newdrive bs=1024kb

Now I have saved the data that was stored on that drive, but what do I do now?

The problem is that even though bios recognized the drive, LVM did not like the UUID and did not start.

Any help is appreciated.

---

### Post by spottedcow on 2008-08-16
I checked the lvm manual found this:

```
REPLACING PHYSICAL VOLUMES
 vgdisplay --partial --verbose will show you the UUIDs and sizes of  any PVs 
that are no longer present.  If a PV in the VG is lost and you wish to 
substitute another of the  same  size,  use  
pvcreate --restorefile filename --uuid uuid (plus additional arguments as 
appropriate) to initialize it with the same UUID as the missing PV.  
Repeat for all  other missing  PVs  in  the  VG.   Then  use  
vgcfgrestore --file filename to restore the volume group&#8217;s metadata.
```


I guess that is all assuming that you backed up the metadata of the original drive with vgcfgbackup although this data appears to be in /etc/lvm/backup/ already.  I'd check the date to make sure it is recent.

---

