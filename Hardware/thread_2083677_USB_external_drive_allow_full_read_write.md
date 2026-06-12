---
title: "USB external drive allow full read write"
date: 2012-11-13
forum: Hardware
---

### Post by agem on 2012-11-13
I'm sure this question has been asked before but how do I allow full read/write access to USB Harddrive?

It was working fine in 12.04 but since I upgraded to 12.10 it's gone screwy. I can copy, write, delete files but now when I run programs that access that drive they no longer work for example, qBittorent will no longer download to the drive, my Virtualbox won't work anymore but programs like XBMC can play files from the drive. 

My fstab looks different now as well with the drive mounted under my user name and I don't think the permissions are right anymore

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda1 :
UUID=d745ca45-2bb3-45a5-aaee-484bf9feee55	/	ext4	defaults	0	1
#Entry for /dev/sdb1 :
UUID=002010DA2010D88C	/media/mega/SAMSUNG	ntfs-3g	defaults,nosuid,nodev,locale=en_AU.UTF-8	0	0
#Entry for /dev/sda5 :
UUID=ef620676-5dff-42f8-9596-22dd1c98fc9c	swap	swap	sw	0	0

```

Any help would be appreciated

---

