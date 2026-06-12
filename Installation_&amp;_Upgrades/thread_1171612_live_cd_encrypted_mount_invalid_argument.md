---
title: "live cd encrypted mount invalid argument"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by dstempfley on 2009-05-27
I am in the process of making modifications to a live cd to support mounting encrypted persistent files.  I have the code for losetup to map  loopback file and cryptsetup to create the mapping to /dev/mapper/test.  But the mount of the device fails.  The directory/file names will change, but the basic mount process should work as written. 

I'm pretty sure the passphrase on the cryptsetup is right, since fstype shows the filesystem as ext2.

Here is some of the relevant output:

fstype /dev/mapper/test
FSTYPE=ext2
FSSIZE=3361198624768

mkdir -p //test.enc
mount -t ext2 -o ro,noatime /dev/mapper/test //test.enc

mount: mounting /dev/mapper/test on //test.enc failed: Invalid argument


If I try to mount the file on the USB device from within a regular system, the drive mounts clean.  

Any help would be greatly appreciated here.

/Dion

---

### Post by anishmp on 2011-03-25
Hi dstempfley, 

I had the same message while booting  a live-build  image, for squashfs 
filesystem.  

fstype reported the correct file system, but mount was not happening. 

Once -t squashfs was introduced in  mount command , it automatically loaded
the squashfs filesystem driver and  mount was successful. 
 
I think the ext2 module is not loaded , Note that fstype doesnt 
need the ext2 module for identifying the FS.  

regards,
anish

---

