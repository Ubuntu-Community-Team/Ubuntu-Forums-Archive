---
title: "[SOLVED] OOPS! accidental parted mklabel on wrong drive"
date: 2008-08-20
forum: General Help
---

### Post by matthewrdamon on 2008-08-20
Today I was following a tutorial and accidentally issued this command:
```
# parted /dev/sdb mklabel gpt
```
and I meant to type this:
```
# parted /dev/sdi mklabel gpt
```

My first thought was to simply change the label back to msdos, which didn't work...

To make matters worse, /dev/sdb is part of an LVM with two other drives, /dev/sdc and /dev/sdd.  

At this point, my partition tables for the drives look like this:

/dev/sdb:
```
# parted /dev/sdb print
Model: ATA Maxtor 6L250R0 (scsi)
Disk /dev/sdb: 251GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


```
/dev/sdc:
```
# parted /dev/sdc print
Model: ATA ST3500630AS (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary               lvm  


```
/dev/sdd:
```
# parted /dev/sdd print
[sudo] password for matt: 
Model: ATA WDC WD2500KS-00M (scsi)
Disk /dev/sdd: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  250GB  250GB  primary                    


```

Furthermore, the vgscan and lgscan look like this:
```
 # vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "media" using metadata type lvm2

# lvscan
  ACTIVE            '/dev/media/music' [230.00 GB] inherit
  ACTIVE            '/dev/media/movies' [309.00 GB] inherit
  ACTIVE            '/dev/media/television' [309.76 GB] inherit

```

I have tired to do a parted /dev/sdb rescue, but to no avail.  And I also ran a gpart scan on the drive, and it ends like this:
```
# gpart /dev/sdb
[sudo] password for matt: 

Begin scan...
Possible partition(DOS FAT), size(1024mb), offset(1803mb)
Possible partition(SGI XFS filesystem), size(316366mb), offset(96000mb)

*** Fatal error: dev(/dev/sdb): seek failure.

```

So far, it seems like I can still access all of my data, but I am scared to reboot or turn off the machine, as I think I will lose the partition table completely.  

My next step, unless anyone has any better ideas is to buy a new drive and back up everything onto that, then restore the LVM as necessary.  Please let me know your thoughts.

Thanks,

Matt

---

### Post by matthewrdamon on 2008-08-20
I just read something stating that all I would need to do is use parted to create a new partition table, just like if I was partitioning a drive from the beginning.  Is this correct?

Now, considering that gpart dies on me every time I run it and that there was only one partition on the disk to begin with, encompassing the whole disk.  Would I be able to just run fdisk or parted and build one large partition from scratch with the partition stretching the whole thing, just like it was before?  Would this solve my problems or just create more?

---

### Post by matthewrdamon on 2008-08-20
I decided to bite the bullet and give it a try.  After all, what could be the harm?

And to my surprise, it worked!.  Marked as solved.

---

