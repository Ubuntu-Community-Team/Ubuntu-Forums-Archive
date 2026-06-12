---
title: "Can't Format external Hard drive Toshiba"
date: 2011-06-10
forum: Hardware
---

### Post by johntkucz on 2011-06-10
Trying to partition new great external hard drive.  It's not used by any program but I get an error that it cant' partition because in use:


```
GParted 0.5.1

Libparted 2.2

Create Primary Partition #1 (ntfs, 600.00 GiB) on /dev/sdc  00:00:01    ( ERROR )
    	
create empty partition  00:00:00    ( SUCCESS )
    	
path: /dev/sdc1
start: 695228940
end: 1953520064
size: 1258291125 (600.00 GiB)
set partition type on /dev/sdc1  00:00:01    ( SUCCESS )
    	
new partition type: ntfs
create new ntfs file system  00:00:00    ( ERROR )
    	
mkntfs -Q -v -L "" /dev/sdc1
    	
/dev/sdc1 is mounted.
Refusing to make a filesystem here!
libparted messages    ( INFO )
    	
WARNING: partition(s) 1 on /dev/sdc could not be modified, probably because it/they is/are in use. As a result, the old partition(s) will remain in use until after reboot. You should reboot now before making further changes.
WARNING: partition(s) 1 on /dev/sdc could not be modified, probably because it/they is/are in use. As a result, the old partition(s) will remain in use until after reboot. You should reboot now before making further changes.
```

---

### Post by StrayEddy on 2011-06-10
I think your problem is, your device /dev/sdc1 is mounted so....

unmount it in terminal: **umount /dev/sdc1**

---

### Post by johntkucz on 2011-06-10
> **StrayEddy said:**
> I think your problem is, your device /dev/sdc1 is mounted so....

unmount it in terminal: **umount /dev/sdc1**


Hey strayeddy.  Thanks for the response and likely helpful and well-calcualted sugggestion/evaluation/diagnosis.

Running that command results in:

```

umount: /dev/sdc1 is not in the fstab (and you are not root)

```

So I did same command with sudo, redid the gparted config and it worked!!!

Thanks!

Question: drives in fstab are regularly mounted?  Would I have to optionally manually add this drive to file system table fstab?  I remember doing something like that in 2007.  What's the benefit of adding a drive to fstab?  Why did it say I wasn't root and wouldn't allow me to unmount the drive without sudo?

Finally, is there a way to partition and format a drive via CLI?  I'd prefer that over gui.  But this formatted, so for now, this seems failry solved.  Thakns, strayeddy!

---

### Post by johntkucz on 2011-06-10
Yeah!!! yay!! Have 599.9 gb free on that partition.  Excellent!  the partitioning worked very well.  On to the next step of truecrypting and then testing compapitibility of the drive across multiple OSes (I went with NTFS file system because with an addon on mac, I am able to read/write to it) sweet this is awesome.  Thanks again, StrayEddy.

For closure, the sucessful details from successful gparted partition:

```
GParted 0.5.1

Libparted 2.2

Create Primary Partition #1 (ntfs, 600.00 GiB) on /dev/sdc  00:00:07    ( SUCCESS )
    	
create empty partition  00:00:01    ( SUCCESS )
    	
path: /dev/sdc1
start: 63
end: 1258291124
size: 1258291062 (600.00 GiB)
set partition type on /dev/sdc1  00:00:01    ( SUCCESS )
    	
new partition type: ntfs
create new ntfs file system  00:00:05    ( SUCCESS )
    	
mkntfs -Q -v -L "" /dev/sdc1
    	
Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
Creating root directory (mft record 5)
Creating $MFT (mft record 0)
Creating $MFTMirr (mft record 1)
Creating $LogFile (mft record 2)
Creating $AttrDef (mft record 4)
Creating $Bitmap (mft record 6)
Creating $Boot (mft record 7)
Creating backup boot sector.
Creating $Volume (mft record 3)
Creating $BadClus (mft record 8)
Creating $Secure (mft record 9)
Creating $UpCase (mft record 0xa)
Creating $Extend (mft record 11)
Creating system file (mft record 0xc)
Creating system file (mft record 0xd)
Creating system file (mft record 0xe)
Creating system file (mft record 0xf)
Creating $Quota (mft record 24)
Creating $ObjId (mft record 25)
Creating $Reparse (mft record 26)
Syncing root directory index record.
Syncing $Bitmap.
Syncing $MFT.
Updating $MFTMirr.
Syncing device.
mkntfs completed successfully. Have a nice day.
```

Also, does anyone know what some of that means?  $MFTMirr and the like?  Unnecessary and probably some advanced driver/file-system details? Thanks.  This is exciting.  So glad I fully formatted and partitioned the drive instead of using it as is with the clunky and cumbersome add-ons and auto-runs it came installed with.  I'm looking forward to building a system with usb3.0 to take advantage of this drive's speed fully.  great!

---

