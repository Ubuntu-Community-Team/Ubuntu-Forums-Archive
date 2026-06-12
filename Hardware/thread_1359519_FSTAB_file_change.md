---
title: "FSTAB file change"
date: 2009-12-19
forum: Hardware
---

### Post by titus2020 on 2009-12-19
I am not able to read cd. Community suggested changes to Fstab file but that changes are not working. 
:confused:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

---

### Post by Maverickprowls on 2009-12-19
There don't appear to be any changes here that relate to a CD or DVD drive.

Using:

```
dmesg | more
```

or

```
dmesg > output.txt
```

should let you find out where your CD or DVD-ROM drive is attached to your system (the second command will dump the output to a text file which you could copy into a forum post here).  From there you might be able to find out what you'll need to enter in your /etc/fstab file.

---

