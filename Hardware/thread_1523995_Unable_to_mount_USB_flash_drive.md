---
title: "Unable to mount USB flash drive"
date: 2010-07-04
forum: Hardware
---

### Post by azangru on 2010-07-04
My mom accidentally removed a USB flash drive from the machine without first clicking on "Eject" or "Safely remove the drive" (I believe, these are the options in Lucid - or was it still Karmic when she did it?). Anyway, as a result, the flash drive doesn't mount in Ubuntu (it's not even recognized as a drive, I don't get any error reports from it, nothing), and Windows 7 recognizes it as an unformatted drive.

Of course, I could simply format the drive under Windows 7, but the thing is, there are some documents or photos - I am not sure what exactly - that my mom says exists only on this drive and she wants them back. Is there any way to trick the improperly removed drive into mounting on an Ubuntu system?

I tried to Google for an answer, but couldn't find anything relevant. Perhaps my key words for searching were wrong - I can't believe this issue hasn't already been discussed.

Thanks!

---

### Post by azangru on 2010-07-04
Just in case, here is the output of the *mount* command:

```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
```

---

### Post by ajgreeny on 2010-07-04
Do you know anyone with, or do you have a windows system?  If so try plugging the usb in that.  Hopefully the windows OS will see it and you can then make sure it is removed safely from windows, not simply pulled out as most people seem to do.  That may allow you to mount the drive in ubuntu.

I admit it is unusual for a usb flash drive which is probably fat32 to suffer this way.  Perhaps ubuntu was still waiting to read/write to it when your mother pulled it out, so the file system is a bit corrupted.

If none of that works you may need to try a manual, forced mount in terminal.

---

### Post by azangru on 2010-07-04
> **ajgreeny said:**
> Do you know anyone with, or do you have a windows system?  If so try plugging the usb in that.  Hopefully the windows OS will see it and you can then make sure it is removed safely from windows, not simply pulled out as most people seem to do.

Tried that before writing here, sorry for not elaborating on that in the first message. No luck. Windows recognized the USB drive as unformatted or corrupted and offered to reformat the drive. So, I'm afraid, this simple option is out.


> **ajgreeny said:**
> If none of that works you may need to try a manual, forced mount in terminal.

Could you please instruct me how to do this?

---

### Post by azangru on 2010-07-04
Some additional info: here is an output of the fdisk -l command:

```
Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000114e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         462     3710983+  83  Linux
/dev/sda2             463         490      224910    5  Extended
/dev/sda5             463         490      224878+  82  Linux swap / Solaris

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf26d47c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1962    15759733+  83  Linux

Disk /dev/sdc: 2051 MB, 2051013632 bytes
64 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Disk identifier: 0x00000434

Disk /dev/sdc doesn't contain a valid partition table

```

I'm not at all familiar with this, but I trust the USB pen drive should be the one marked as /dev/sdc?

---

### Post by davec64 on 2010-07-04
Looks like it is /sdc.

Have a look at TestDisk:

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

It will rebuild the partition table so you can get to the data. I've used it successfully on a hard disk, but I think it will work on a usb drive.

It's a CLI tool but you should be able to find a howto for it.

EDIT:

Test Disk is in the repositories, so:

```
sudo apt-get install testdisk
```

---

### Post by azangru on 2010-07-04
> **davec64 said:**
> Have a look at TestDisk:

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

It will rebuild the partition table so you can get to the data. I've used it successfully on a hard disk, but I think it will work on a usb drive

Yes, that worked like a charm! Thank you very much!

---

