---
title: "worrying boot up error message"
date: 2011-12-04
forum: Hardware
---

### Post by UncleMonty on 2011-12-04
"An error occurred whilst mounting /media/sdb1

Please s to skip mounting or m for manual recovery"


This has happened twice now. I would press 'm' but have no idea what to do next!

---

### Post by Rubi1200 on 2011-12-04
Please post the results of the boot info script so we can get a better overview of what is going on.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by drs305 on 2011-12-04
Since the referenced mount is in /media, have you just tried pressing S to skip mounting? 

It could be as simple as a device that is no longer plugged in but is listed in fstab. If it boots, open your /etc/fstab file and look for a device referenced in the error message. Place a comment symbol # at the start of the file and save it until we/you figure out what is wrong with it.

---

### Post by UncleMonty on 2011-12-05
> **Rubi1200 said:**
> Please post the results of the boot info script so we can get a better overview of what is going on.

There is a link at the bottom of my post with instructions.

Thanks.

```
[noparse]

= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    265024 of the same hard drive for core.img, but core.img can not be found 
    at this location.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

[/noparse]
```

---

### Post by drs305 on 2011-12-05
Only part of the RESULTS.txt file was posted. 

Please include the entire contents. You can either edit your previous post and copy the content between the 'code' tags, or make a new post. 

Paste the contents and highlight them, then press the # icon in the post's menu. This will place the content within 'code' tags, which makes it easier to read. Thanks.

---

