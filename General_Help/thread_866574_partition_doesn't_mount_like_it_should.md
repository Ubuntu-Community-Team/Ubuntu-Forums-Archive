---
title: "partition doesn't mount like it should"
date: 2008-07-21
forum: General Help
---

### Post by Sunborn on 2008-07-21
So I had a problem with my X11 config file so I had to boot to command line to change the file back. However, for some reason the system was loading / with read-only flag, assuming because that is the only way mount would let it work. Since I couldn't edit files and change xorg.conf to the backup, I decided to boot the live CD and hopefully it would mount as writeable. No luck, the following worked:

sudo mount -r -t jfs /dev/sda2 /media/disk-2

but the writeable mount didn't. Yes I did unmount the drive to try again.

sudo mount -w -t jfs /dev/sda2 /media/disk-2

Yet, when the X server is working properly the root filesystem mounts fine with writeable access. This can't be something with X can it? What does X have to do with mounting a JFS filesystem? I have no idea. Just freaking weird. Is JFS weird in some way. I just chose it because I wanted a journaling filesystem that wasn't ext3. Did I make a bad choice? I mean if I hadn't been able to revert my hardware changes I would have been up the creek not being able to change the xorg.conf since I couldn't mount /dev/sda2 as anything other than read-only.

---

### Post by Mister.Vash on 2008-07-22
Did it give you any error messages for the mount?

It could be that it needs a check - if it does, boot from the live cd then run
jfs_fsck /dev/sda2

Which should take care of it.  If it doesn't post the message that you get when the mount fails

---

### Post by Rocket2DMn on 2008-07-22
Can you please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
from within your normal boot (not a LiveCD).  If you have to do it from a LiveCD, mount the root filesystem and post the fstab from the install, not the LiveCD.

---

### Post by Sunborn on 2008-07-23
Sorry, I can't seem to duplicate the problem. Everything was exactly the same, except for the crash before the problem which was caused by no battery to my laptop. I tried everything but if it happens again I will post those outputs.

---

### Post by epsilon359 on 2008-08-20
I've been experiencing the same problem on and off. It happens randomly when I boot, the filesystem just becomes read-only. A few reboots later, the filesystem can magically be written to again and all works as expected.

---

