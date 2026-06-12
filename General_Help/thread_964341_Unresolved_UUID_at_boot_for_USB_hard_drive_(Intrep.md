---
title: "Unresolved UUID at boot for USB hard drive (Intrepid)"
date: 2008-10-30
forum: General Help
---

### Post by dlodge on 2008-10-30
I just upgraded to 8.10 desktop, with a clean install on a fresh partition.  The routine boot sequence fails and I go to a maintenance shell. After hitting CTRL+D for a routine boot, all partitions including my USB hard drive are correctly mounted.

Error message from /var/log/fsck/checkfs log:
fsck.ext3: Unable to resolve 'UUID=8ae890ad-004c-4da7-81a7-c49e6ff6501a'
fsck died with exit status 8

The UUID identified in the log is the ID from /etc/fstab of my USB hard drive:
# /dev/sdb1
UUID=8ae890ad-004c-4da7-81a7-c49e6ff6501a  /media/netdisk320  ext3 relatime  0  2

'blkid' confirms:
/dev/sdb1: LABEL="netdisk320" UUID="8ae890ad-004c-4da7-81a7-c49e6ff6501a" SEC_TYPE="ext2" TYPE="ext3"

'vol_id -u /dev/sdb1[' also confirms:
8ae890ad-004c-4da7-81a7-c49e6ff6501a

This is a USB hard drive, and I had no problem with it under hardy.

Any thoughts?

---

### Post by Yellow Pasque on 2008-10-30
It almost sounds like a race condition where fsck tries to run before something crucial to accessing the USB drive is loaded (e.g. a kernel driver).

---

### Post by dlodge on 2008-10-30
> **Temüjin said:**
> It almost sounds like a race condition where fsck tries to run before something crucial to accessing the USB drive is loaded (e.g. a kernel driver).
You are correct, it is a race condition.  The problem persists after moving the USB device to the end of the fstab.  However, if a CD is present in the drive, the problem goes away.

Is there any way to place some type of wait in the fstab? In the meantime I think I will disable the automatic fsck.

---

### Post by Yellow Pasque on 2008-10-30
EDIT: see the next post

---

### Post by Yellow Pasque on 2008-10-30
Actually, this sounds exactly like your bug:
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/182616](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/182616)

---

### Post by dlodge on 2008-11-17
> **Temüjin said:**
> Actually, this sounds exactly like your bug:
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/182616](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/182616)
Thanks, adding "sleep 5" to the beginning of /etc/init.d/checkfs.sh worked for me.

I don't like the concept of the extra wait time in my boot scripts, so I experimented with shorter delays. 1 second was too short, 2 seconds would occasionally give an error. 3 seconds seems to be working ok.

How much parallelism is in the boot scripts? Does tinkering with the checkfs sleep time even matter?

---

