---
title: "#mount error mount: wrong fs type... etc."
date: 2009-09-15
forum: Hardware
---

### Post by sunpyo on 2009-09-15
I'm having a lot of trouble trying to find out the filesystem of my raid5 server. I have 3 of the 4 disks, which fdisk tells me is functioning properly. I have finally recreated my raid5 by using the Live Bootable CD and this:
 
```
#mdadm --assemble --scan -f
```
 
After doing so I had created the filesystem which is /dev/md0 and also the data volume which is /dev/md2. I can look around the filesystem and such however I cannot access the data volume. I know where the mount point of the data should be, which is /media/disk. In my file browser I am able to see the drive, but I cannot open it. All it says is "Software RAID Drive". I need to access this drive in order to recover some data I have lost.
 
I didn't make this raid5, WD did. It came from a NAS which creates its own RAID5 through linux. I knew this because in my quest to restore this thing, I used countless windows programs and all told me that this had an ext3 filesystem.
 
So I tried multiple things:
 
```

#mount /dev/md2 /media/disk/shares
#mount -t ext3 /dev/md2 /media/disk/shares
#mount -t ntfs /dev/md2 /media/disk/shares
#mount -t xfs /dev/md2 /media/disk/shares

```
 
Each will give me the error:
 
```

wrong fs type, bad option, bad superblock on /dev/md2, missing codepage or helper program, or other error
In some cases useful info is found in syslog -try dmesg | tail or so

```
 
dmesg told me that they couldn't apply any of the filesystems to the Raid5 data volume. Also fdisk -l shows me this as well:
 
```

Disk /dev/md2 doesn't contain a valid partition table

```
 
I'm really having a very difficult time with this. If anyone has any ideas, please contact me at [EMAIL="hong.sunpyo@gmail.com"]hong.sunpyo@gmail.com[/EMAIL] or post here. Thanks.

---

### Post by sunpyo on 2009-09-15
I also have not worked with the --create action yet. Will this corrupt my information or my raid. I know that my raid is /dev/md2, so could I do something like..
 
```
 
#mdadm --create --verbose /dev/md3 --level=5 --raid-devices=4 missing /dev/sdb4 /dev/sdc4 /dev/sdd4

```
 
And would this delete any progress I've made? Thanks!

---

