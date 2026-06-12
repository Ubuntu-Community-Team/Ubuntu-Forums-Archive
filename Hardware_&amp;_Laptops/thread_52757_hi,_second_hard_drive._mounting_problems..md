---
title: "hi, second hard drive. mounting problems."
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by graigsmith on 2005-07-28
hi i am having problems mounting my second hdd.  i formatted it with reiserfs.  i can mount it, but it is read only. 

i just want to get it in fstab, and have it run so my own user account can access it. 

im trying to mount it in ~/extra.space

here is what my fstab looks like.  hdb1 is mounting in my home directory, but with the wrong permissions.  what options do i add to get it to mount so i can use it?

thanks. -Graig.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   	<type>  	<options>       		<dump>  <pass>

proc            /proc           	proc		defaults        		0 0
/dev/hda1       /               	ext3    	defaults,errors=remount-ro 	0 1
/dev/hda6       /home           	ext3    	defaults        		0 2
/dev/hda5       none            	swap    	sw              		0 0

/dev/hdb1	/home/graig/extra.space	auto		user,rw,auto			0 3

/dev/hdc        /media/cdrom0   	udf,iso9660 	ro,user,noauto  		0 0
```

---

### Post by graigsmith on 2005-07-28
it changes the folder i made in my home directory to a root owned folder.

---

### Post by graigsmith on 2005-07-28
wait, nm, all i had to do was take ownership of it. and it works perfectly now. and i just changed the options simply to defaults.

---

