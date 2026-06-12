---
title: "Mount home one existing partition"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by iboot on 2009-10-30
I installed Karmic on an existing machine that had Jaunty. I wiped out the root partition but did not mount the /home partion during the installation. 

How do I mount the older /home partion as the new /home?

```

~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            115417772   2363328 107191528   3% /
udev                   1417844       292   1417552   1% /dev
none                   1417844      1224   1416620   1% /dev/shm
none                   1417844        96   1417748   1% /var/run
none                   1417844         0   1417844   0% /var/lock
none                   1417844         0   1417844   0% /lib/init/rw
/dev/sda7            180709612  23498084 148031992  14% /media/a44bd342-a04e-4433-91d3-218d15f7967d

```My /etc/fstab :

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=37f94ded-dec6-4225-90a1-859cd099ffd5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=342feef3-b73f-45ee-ad03-7d1f9c0638b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

