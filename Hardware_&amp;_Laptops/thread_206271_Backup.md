---
title: "Backup"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by penguinchrissy on 2006-06-29
I'm trying to back up a NTFS partion to a external harddrive thats USB 2.0 I also need to be able to write to the external harddrive. Is there a program that will allow me to do this or can I go about this with code either way is fine.

---

### Post by woedend on 2006-06-29
To get more information here...
you want to copy information(backup) FROM a ntfs TO a usb hard drive.  Is this usb hard drive NTFS also?  If you haven't used this usb hard drive yet, definetely make it FAT32 if you can, it seems to work the best between NTFS and linux, since writing to ntfs is a pain in linux.  Anyhow, are you looking for this to be automated, or just to do it at your discretion?
If you just want to move them over, nautilus will do the job just fine.
If you want it automated, I would make a small script cronjob to do it.  Let me know what more you are looking for.

---

### Post by penguinchrissy on 2006-06-29
The external one is NTFS formatted and I would really like to not have to format it. I dont' care if its automated or not I just want to be able to do it once so I can format the hard drive.

---

### Post by woedend on 2006-06-29
[https://wiki.ubuntu.com/Lkraider/NtfsFuse?highlight=%28ntfs%29%7C%28%2Bfuse%29](https://wiki.ubuntu.com/Lkraider/NtfsFuse?highlight=%28ntfs%29%7C%28%2Bfuse%29)

just keep in mind that it CAN ruin the filesystem on the other hard drive.
Let me know if you have any questions

---

### Post by penguinchrissy on 2006-06-29
Ok I tried to follow the steps in the howto nothing was working and in the process lost all my mounts. Get most of the mounts for my drives back but my computer won't recongize my USB hard drive any more. Why? and do I have to mount both through fuse or just one.

---

### Post by woedend on 2006-06-29
sorry i should have remembered to say just in case, /dev/hda1 is just an example, yours will not be that(maybe hdb1 or sda1?)...and also when adding user to the ntfs group , replace with your username(hey, i've done this)
secondly, you can mount them both that way.

---

### Post by penguinchrissy on 2006-06-30
I've done everything so far and its close to working but it says that ntfs-fuse is an unknown file type ```
sudo apt-get install libfuse2 ntfsprogs fuse-utils
``` I tried doing that again to see if it didn't update the lib but it saying it updated nothing my fstab looks like this
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb5 /media/hdb5 ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /media/hdb1 ntfs-fuse auto,uid=1001,gid=1002,umask=0027       0       0

```
the hdb1 being my test drive for this and hdb5 being the one I want to back up (just want to see what the risk is before backing up)

---

### Post by woedend on 2006-06-30
does hdb5 mount fine this way?
also, is you uid and gid right?
by default, the first user is uid=1000
but both uid and gid aren't needed..generally I use just one or the other.

Does ntfsmount work...such as
sudo ntfsmount /dev/hdb1 /media/hdb1 -o umask=0007

---

