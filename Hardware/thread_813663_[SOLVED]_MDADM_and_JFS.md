---
title: "[SOLVED] MDADM and JFS"
date: 2008-05-31
forum: Hardware
---

### Post by CNLiberal on 2008-05-31
I am trying out MythBuntu.  So far, it's not working correctly.  I'm having problems with setting a static IP, my nVidia FX5200 doesn't want to work, and most importantly, my MDADM RAID 5 array with nearly 2TBs of data won't mount.  Here's the deal.  I tried mounting the /dev/md0 in /etc/fstab.  Here's the relevant lines:

/dev/md0        /storage        jfs     defaults        1       2

I don't know if those are right, I think they are.  It is definitely a JFS array.  The location does exist.  Here's what I get when I do a mount:

joltman@mythbackend:/dev$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

So I run that command...Here's the output.

[  749.804430] md: invalid raid superblock magic on sda
[  749.804441] md: sda does not have a valid v0.90 superblock, not importing!
[  749.804903] md: md_import_device returned -22
[ 1161.711437] JFS: nTxBlock = 8088, nTxLock = 64710


OK.  Not a good thing.  I run this command:

joltman@mythbackend:/dev$ sudo fsck -t jfs /dev/md0
fsck 1.40.8 (13-Mar-2008)
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 5/31/2008 0.10.58
Using default parameter: -p
The current device is:  /dev/md0
Superblock is corrupt and cannot be repaired 
since both primary and secondary copies are corrupt.  

 CANNOT CONTINUE.

That is really not a good thing.  What the heck do I do next?  I can't lose my info.  I know it's in there cuz it was mounted just fine earlier on an FC4 box.  Thanks for your help!

Jim

---

### Post by CNLiberal on 2008-05-31
Does anyone know what this could be?  I really can't lose all my data.  Any help would be appreciated.  Thanks!

Jim

---

### Post by CNLiberal on 2008-05-31
OK, my bad.  I installed MDADM and then magically expected it to find and setup my array.  I rebooted, and all is well.  Sorry for the interuption!

---

