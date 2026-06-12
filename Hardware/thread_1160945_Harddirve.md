---
title: "Harddirve"
date: 2009-05-16
forum: Hardware
---

### Post by Ohwii on 2009-05-16
Hi Guys,

after a long trial and error I finally got ubuntu to find my share hard drive with windows.
Unfortunatly all my files and folders are gone. I cannot see them but they still take up space. In windows and in ubuntu both show a empty partiotin. Even ubuntu shows that it is a 440 GB partiotion, but there is only 410 GB free. 
 

can someone help please.

 here is my messy fstab 

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> 	<mount point> 		  <type>  	<options>       <dump>  <pass>
proc            	/proc           	proc   		 defaults        0       0
# / was on /dev/sda2 during installation
UUID=aed2a5a7-4312-4177-a4c3-1048e2a5abf5 /               ext3    relatime,errors=remount-ro 0       1
# /share was on /dev/sda4 during installation
/dev/sda4	/media/share          	vfat   	defaults,uid=1000,gid=1000	0       0
# swap was on /dev/sda3 during installation
UUID=6b6e28b6-965a-4026-9e3f-6e72c28c5618 none            swap    sw              0       0
/dev/scd0      		 /media/cdrom0  	 udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0       		 /media/floppy0  	auto    rw,user,noauto,exec,utf8 0       0
```

Thanks a lot Oh wii

---

### Post by Ohwii on 2009-05-16
Bump anybody?

---

### Post by Ohwii on 2009-05-17
bump. Please can anybody help

---

