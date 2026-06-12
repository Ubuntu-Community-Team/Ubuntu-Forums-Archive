---
title: "Need help automounting USB drive at boot - emergency mode"
date: 2016-08-27
forum: Hardware
---

### Post by jschwalbe on 2016-08-27
Greetings. New user of Ubuntu and having some trouble getting a USB drive to mount automatically at reboot.

Some background:
I'm running 16.04 (new install) on a Mac Mini Core 2 Duo. *(Kudos, by the way at how easy it was to install! Installed 14.04 via CD then upgraded immediately. Seamless.) *With this setup I am planning to run ```
ownCloud
```. The internal drive is too small so I'm using a USB WD MyBook, formatted as ext4. With the line as below in fstab, on reboot the computer stalls out and drops me into emergency mode. I have to comment out the fstab line in question and then it will boot back up. Without the fstab line, the drive will still mount in /media/<username>/<drivename> but I'd much rather have it mount at /data instead (without having to worry about which user logs in first...)

/etc/fstab:
```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=d99eee12-def0-453d-b092-130a8a908569 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0cb9513d-6fc8-4c29-8f41-b0fe3c964162 none            swap    sw              0       0
# USB drive = WD3TB
UUID=642aedf0-d60f-47be-8177-20de9997e984 /media/WD3-Epic    ext4    user,owner    0    2
```

Of note, with the above file, when I type 
```
sudo mount -a
```
it appropriately mounts the drive in the correct location, as specified in the file above.

Can any gurus help me understand what I'm doing wrong?  Many thanks!

---

### Post by yancek on 2016-08-27
I always use the /mnt directory for fstab entries although I'm not sure it matters.   Obviously, leaving the standard where it mounts under /media/user can create problems.  What's the purpose of the 'owner' option, never seen that used before.  Do you get any message on boot when it failes?

> /dev/sda11 /mnt/data ext4 defaults 1 2

---

### Post by jschwalbe on 2016-08-28
Well I tried a few different settings with fstab but each failed. Eventually I found success with the following crontab command:


```
@reboot mount /dev/sdb2 /data

```

Seems to work after a few reboots!

---

### Post by Bucky Ball on 2016-08-29
If it keeps working, please see the last line and link in my signature to mark the thread 'solved' and help others. Well done. :)

---

