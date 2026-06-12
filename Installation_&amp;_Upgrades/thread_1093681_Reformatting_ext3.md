---
title: "Reformatting ext3"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by TheBlackSun on 2009-03-11
I have a bunch of partitions currently formatted as ext3 with custom ext3 settings such as different journaling methods and volume labels. I want to either erase or reformat each partition so that i can install a fresh version of Ubuntu 8.10. Is there a way to reformat each ext3 partition while keeping its customized options or should i just erase it all? What would be the cleanest method of erasing all the contents of the partitions?

---

### Post by taurus on 2009-03-11
If you want to wipe clean the partitions, you can use gparted (System -> Administration -> Partition Editor) from Ubuntu LiveCD.

---

### Post by lensman3 on 2009-03-11
You can just format over it.

1) Umount the paritions you want to format "umount /dev/sdxx"

2) /sbin/mkfs.ext3 -v /dev/sdxx"     (Do this command for each of the partitions.  One of the options on mkfs is to write blanks onto the  disk, but that can take a loooong time.

3) Then remount the partitions using "mount /dev/sdxx /<mount point>" and also update the /etc/fstab file so the partition will mount automatically during boot.

I would suggest that you format the new disks using the new ext4 format.  It appears to be more robust and you can defrag the disks.  It is also a journaling file system.  The format command is "/sbin/mkfs.ext4".

To see all the options for mkfs, then do "man mkfs.ext3" and "man mkfs.ext4".  It is OK to mix and match file system types.

---

### Post by TheBlackSun on 2009-03-12
Thanks for the replies. I really didn't want to have to use mkfs.ext3 since it will lose my volume labels, mount options, and journaling method; however, there seems to be no easy way and upgraded to ext4 does sound like a good idea to me. I was not aware that it was prime time already. I guess i'll go with a Jaunty install and ext4.

---

