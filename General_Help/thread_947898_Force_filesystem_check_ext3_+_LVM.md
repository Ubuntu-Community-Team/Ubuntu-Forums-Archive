---
title: "Force filesystem check ext3 + LVM"
date: 2008-10-14
forum: General Help
---

### Post by _sAm_ on 2008-10-14
I have a simple fileserver with Ubuntu Server(hardy), LVM, and ext3, and I don't turn it off often. That means that the filesystem check is also seldom. 

How can I force the filsystem check on next reboot, on _all_ partitions(and LV).I have googled and found these suggestion to do this:
sudo touch /forcefsck
shutdown -rf now
shutdown -rF now

I also want to make it check more often then default, would this be ok: 
sudo tune2fs -c 10 -i 2w /path to partition

I am a bit unsure about the path since I use LVM. Should it be what df -h tells me or fdisk -l? I guess df -h since the ext3 is on top of the LVM. 

Thanks for any help:-)

---

### Post by _sAm_ on 2008-10-15
bump

---

### Post by amac777 on 2008-10-15
You've probably seen this thread already but it seems to explain what your looking for:

[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

About getting all the partitions to scan, note the second post in that thread that you need to amend the fstab to indicate those partions should be scanned.

Also, for partitions other than your root partition, you could just umount them and manually run fsck on them. So no need to reboot the system to check the the non root partitions.

---

