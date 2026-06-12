---
title: "[SOLVED] how to access the old /home partition?"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by aum11 on 2009-01-02
Just installed 8.10 and specified that the new install (on sda3) use the previous /home on sda6.

When rebooting after the install, the original /home is not being accessed.  It must be using a new home in sda3....none of the old home data is seen.  It is all still there, as verified via gparted.

 Can You please advise me how to change the /home to be at sda6.

Thanks.

---

### Post by aum11 on 2009-01-02
when i checked out /etc/fstab it shows that /home is at sda6.  So why can't I access any of the files there?  Any ideas?  Thanks.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=7789e400-3055-4200-af86-7502d77a78a4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=90bf5c0f-dab3-4643-b0c1-d96d1832729f /home           ext3    relatime        0       2
# /dev/sda5
UUID=f330592f-0bd6-4761-8207-487cecabbdbc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by aum11 on 2009-01-02
Problem solved...I am installing this on a friends computer and I was looking under the wrong user name.

Oh well!!!!

---

### Post by cdtech on 2009-01-02
Check the UUID and see if it's the correct one:
```
blkid
```
You could just do away with the UUID and use the "/dev/?" instead......

---

### Post by logos34 on 2009-01-02
> **aum11 said:**
> Problem solved...I am installing this on a friends computer and I was looking under the wrong user name.

Oh well!!!!

what did you do, reinstall using a different user name?

---

### Post by aum11 on 2009-01-02
Simply had to change the home directory to point to the correct user's home

---

