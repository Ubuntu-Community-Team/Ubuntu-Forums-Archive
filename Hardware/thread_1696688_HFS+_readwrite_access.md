---
title: "HFS+ read/write access"
date: 2011-02-27
forum: Hardware
---

### Post by j.biddy on 2011-02-27
I've been having some system failures so I'm trying to back up data to an external USB hard drive before I reinstall and such. I've trying to move data from multiple internal HDDs to the one external USB device. The USB hard drive is not mine, it is a friend who uses it to back up data from their MacBook. I've used this hard drive before to store files on, so I know that you have to turn the journaling off of HFS+ drives before they can work in other OSes usually, so I've done this. 

The drive actually let me back up some data, but mysteriously began giving me read-only errors about halfway through the back up process. I can for the life of me figure out why it all of a sudden thinks the drive is read-only. I ran mount and the drive came back as rw and with no uid. I tried umounting and mounting it via the command line but I got an error about the wrong type of HFS or something.

---

### Post by j.biddy on 2011-02-28
I have solved this problem. Apparently if the disk is improperly unmounted (whatever that means?) Linux will mount the file system as read-only until it has been error checked. I installed fsck.hfsplus and ran the following command:
```
sudo fsck.hfsplus /dev/sdXY
``` 

After a restart I was able to mount the external hard drive with read-write permissions and copy the rest of my files.

---

