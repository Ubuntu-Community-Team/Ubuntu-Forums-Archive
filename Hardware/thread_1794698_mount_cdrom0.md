---
title: "mount cdrom0"
date: 2011-07-01
forum: Hardware
---

### Post by kersandt on 2011-07-01
Hi all you experts

I'm trying to get my external cdrom (on USB)to work. I get message special device /dev/scd0 does not exist
.  when typing etc/fstab it says permission denied.
When typing more etc/fstab I get:

# /etc/fstab: static file system information. 
# 
# Use 'blkid -o value -s UUID' to print the universally unique identifier 
# for a device; this may be used with UUID= as a more robust way to name 
# devices that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# / was on /dev/sda1 during installation 
UUID=e8b7d348-e5c8-4dbf-bbea-3582c8f7d4d5 /               ext4    errors=remount 
-ro 0       1 
# swap was on /dev/sda5 during installation 
UUID=586e2c81-301f-4b85-aa72-5a4d9d9cbb32 none            swap    sw            
  0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
# /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0 


WHEN I TYPE nano etc/fstab I get:-


# /etc/fstab: static file system information. 
# 
# Use 'blkid -o value -s UUID' to print the universally unique identifier 
# for a device; this may be used with UUID= as a more robust way to name 
# devices that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# / was on /dev/sda1 during installation 
UUID=e8b7d348-e5c8-4dbf-bbea-3582c8f7d4d5 /               ext4    errors=remoun$ 
# swap was on /dev/sda5 during installation 
UUID=586e2c81-301f-4b85-aa72-5a4d9d9cbb32 none            swap    sw           $ 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
# /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0 


which all means noting to me except that something is wrong.

Can some PLEASE help me sort this lot out????

---

