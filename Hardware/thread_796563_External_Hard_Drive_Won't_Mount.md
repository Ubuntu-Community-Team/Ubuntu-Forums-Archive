---
title: "External Hard Drive Won't Mount"
date: 2008-05-16
forum: Hardware
---

### Post by nkobel003 on 2008-05-16
Hello All,

I have a Western Digital 500 GB external hard drive. It is divided into 5 partitions: an ntfs portion that I mainly use it for, a fat32 that I use for backups, and 3 other fat32's that are empty for future linux installations.

When I plug in the hard drive, it give me this error message:
> 
Cannot mount volume
Invalid mount option when attempting to mount the volume 'WD500'.


Here is my fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type> 			<options>  			<dump>  <pass>
proc		/proc		proc			defaults			0	0
/dev/sda3	/media/WD500	ntfs			noauto				0	0
UUID=4d1a7194-1abf-40c1-bdcb-7605a7b4b114 /	ext3    relatime,errors=remount-ro 	0       1
/dev/sda4	/media/BACKUP	fat32			noauto				0	0
UUID=bba55c7f-9c54-46db-bac1-c40df0cb823d none  swap    sw  		    	        0       0
/dev/scd0       /media/cdrom0   			udf,iso9660 user,noauto,exec,utf8 0       0

```

I was able to mount my drive in 7.10, and for the first couple of boots in 8.04, but now it won't let me at all.

Does anyone have any clues?

Thank you,

Nick

---

### Post by EXCiD3 on 2008-05-18
What is the output of ```
sudo fdisk -l
```

---

