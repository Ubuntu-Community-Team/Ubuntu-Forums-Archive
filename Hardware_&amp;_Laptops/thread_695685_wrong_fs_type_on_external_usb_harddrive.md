---
title: "wrong fs type on external usb harddrive"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by dizzy_ on 2008-02-13
I have an HP USB hard drive which I formatted ext3 when I got it. I needed to transfer some files to a friends Windows system forgetting that it wasn't FAT. When I plugged it in to the Windows computer nothing happened so I needed to use Administrative Tools/Computer Tools/DIsk Management to mount it and assign it a drive letter. Anyway, I then realized my mistake and plugged it back into my Linux computer. 

I get this:

 sudo fdisk -l 

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    6  FAT16

###

james-laptop:~% sudo mount /dev/sdb /media/disk
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

###

james-laptop:~% dmesg | tail
[  104.055000] sdb: assuming drive cache: write through
[  104.057000] SCSI device sdb: 312581808 512-byte hdwr sectors (160042 MB)
[  104.059000] sdb: Write Protect is off
[  104.059000] sdb: Mode Sense: 38 00 00 00
[  104.059000] sdb: assuming drive cache: write through
[  104.059000]  sdb: sdb1
[  107.682000] sd 3:0:0:0: Attached scsi disk sdb
[  107.708000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  247.680000] EXT3-fs error (device sdb): ext3_check_descriptors: Block bitmap for group 880 not in group (block 0)!
[  247.681000] EXT3-fs: group descriptors corrupted!

###

james-laptop:~% sudo mount -t ext2 /dev/sdb1 /media/disk
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

###

Will this command fix it:
mkfs -t ext2 /dev/sdb1

Any help would be appreciated.

---

### Post by taurus on 2008-02-13
The drive is vfat so you can't mount it as ext2!

```
sudo mkdir /media/disk
sudo mount -t vfat /dev/sdb1 /media/disk -o umask=000
```

---

### Post by dizzy_ on 2008-02-13
i get the same error. 

sudo mount -t vfat /dev/sdb1 /media/disk -o umask=000

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

did you read the first paragraph? i had originally formatted it as ext3 but when i tried to manually mount it in windows, somehow it changed something on the drive. if it was vfat my windows machine would have automatically mounted the drive, no?

---

### Post by taurus on 2008-02-13
Do you want to reformat it to ext3 again?

```
sudo mke2fs -j /dev/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
df -h
```

---

### Post by az on 2008-02-13
[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)
[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

You can always try to data-carve the files that were there.

---

