---
title: "[lubuntu]14.04.1 I cannot use a newly created ext4 partition on USB drive"
date: 2014-09-09
forum: Hardware
---

### Post by elpidiovaldez5 on 2014-09-09
I created a new ext4 partitition on a USB drive using gparted.  The partition mounts correctly as /media/paul/Backups.  pcmanfm reports that it is owned by root and that 'change content' is only allowed by owner.  

```

paul@thetis:~$ ls -l /media/paul/Backups
total 16
drwx------ 2 root root 16384 Sep 10 01:47 lost+found

```

The output from 'mount' shows:
/dev/sdb1 on /media/paul/Backups type ext4 (rw,nosuid,nodev,uhelper=udisks2)

I have tried to change permissions and ownership in various ways:

```
/dev/sdb1 on /media/paul/Backups type ext4 (rw,nosuid,nodev,uhelper=udisks2)

sudo chown -R paul:paul /media/paul/Backups
sudo chmod 666 /media/paul/Backups
sudo chmod 777 /media/paul/Backups

```

All these efforts result in a broken file system, which subsequently refuses to mount.  I found that the journal was corrupted.  The problem can be repaired by:
sudo fsck /dev/sdb1

'mount' shows that the partition is mounted rw, however the permission changing commands fail complaining that file system is read-only.
e.g.
```
sudo chown -R paul:paul /media/paul/Backups
chown: changing ownership of ‘/media/paul/Backups/lost+found’: Read-only file system
chown: changing ownership of ‘/media/paul/Backups’: Read-only file system

```


Any help in using this drive would be very welcome !

---

### Post by TheFu on 2014-09-10
Only run fsck on an unmounted file system.
Set the ownership/permissions on the mount point BEFORE mounting.
Mount it.
Check that the owner/permissions of the mounted location are what you want, then use chmod -R as desired.

I've always had issues with USB connected devices.  There is something flaky about it.  Fixing the connection usually requires a reboot from power-off, then a few days later, the connection is lost again. Doesn't matter which USB2/USB3 or if using onboard or addon USB cards.  My systems are VM servers, so a reboot isn't convenient ... ever.

Check the log files for hints on the issue - hopefully it isn't the USB connection on yours too.  dmesg is helpful.

---

