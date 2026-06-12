---
title: "Mounting - udisksctl: command not found"
date: 2014-03-16
forum: Hardware
---

### Post by LuigiMazzini on 2014-03-16
Hello,
I would like my system  to auto-mount a partition where I store data downloading with Transmission.
```
[COLOR=#333333][FONT=UbuntuMono]udisksctl mount --block-device /dev/disk/by-uuid/<uuid of my_partition>[/FONT][/COLOR]
``` doesn't work: ```
udisksctl: command not found
```.
What can I do to automatically mount my_partition on startup?

---

### Post by Elfy on 2014-03-16
Add it to fstab and it will be mounted when you boot.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Simply put - make sure somewhere is available for it to mount, I use /mnt and then add a line to fstab.

Mine looks like this 
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=d35579ba-d298-4976-a4fb-92984f476109 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c1ce2207-99dc-4481-bb50-6af96099eca9 none            swap    sw              0       0

##media
UUID=14ee47cc-54cb-4887-8773-fd53121efe10 /mnt/music ext4 defaults 0 2
UUID=aae5bb07-a350-4a7d-a115-2593b61e8fa1 /mnt/Data ext4 defaults 0 2
UUID=aa678306-da8e-4a7d-a2a2-e1de2d3cdedc /mnt/Spare ext4 defaults 0 2
```

```
hob@hobtahr:~$ ls /mnt
Data  music  Spare
```

---

### Post by LuigiMazzini on 2014-03-16
Done. Thanks.

---

### Post by Elfy on 2014-03-16
welcome :)

---

