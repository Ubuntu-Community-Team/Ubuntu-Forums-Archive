---
title: "CDROM not recognized"
date: 2011-08-24
forum: Hardware
---

### Post by Hellhound4 on 2011-08-24
Ok so my cd/dvd player is not being recognized by the computer. It will open and close if I hit the button but the 'eject' command outputs this.

michael@michael-laptop:~$ eject cdrom
eject: tried to use `/media/cdrom0' as device name but it is no block device
eject: tried to use `/mnt/cdrom' as device name but it is no block device
eject: unable to find or open device for: `cdrom'
michael@michael-laptop:~$ 

same if I use sudo.

The contents in fstab are:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=bd99f807-2402-4b01-875a-15a29dcf6274 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=69184005-13fd-4709-b312-b57d0546c9f6 none            swap    sw              0       0
/dev/scd0/media/cdrom   udf,iso9660 user,noauto,exec,utf8 0 0

I've tried to navigate to /dev/scd0/media/cdrom but it isn't there. Ive read tons of posts on this but none of the solutions I've tried have worked. The computer is an hp dv6000 using Lucid I believe.

On startup the load screen tells me that the device at 9660 utf 8 is not ready and I can press S to skip M to manually recover or wait. It doesn't work no matter how long I wait.

---

