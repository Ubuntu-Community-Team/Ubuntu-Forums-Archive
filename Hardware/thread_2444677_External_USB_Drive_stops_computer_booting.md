---
title: "External USB Drive stops computer booting"
date: 2020-06-02
forum: Hardware
---

### Post by rsteinmetz70112 on 2020-06-02
I have been setting up some additional backup. One scheme was in add a 2GB external drive and back up current working files to it. 

However I've found that if i reboot the machine with the drive connected the computer will not boot all the way. It gets partially through loading Ubuntu and then fails in emergency mode and prompts for Cntrl D to continue or the root password. I get some error messages during boot about lvm and the other drives do have lvm volumes on them. If I boot without the drive connected it boots fine. 

I do not have the drive in the fstabs I haven't decided how I want it set up also if the drive is connected at boot is always gets assigned as /dev/sda. The Drive is a USB3 Seagate Basic without external power.

---

### Post by TheFu on 2020-06-02
Post your fstab.

---

### Post by rsteinmetz70112 on 2020-06-03
The drive in question - /dev/sda is not referenced in the fstab.


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/mapper/system-root /       ext4 defaults 0 1
/dev/mapper/system-var /var   ext4 defaults 0 2
/dev/mapper/system-tmp   /tmp   ext4 defaults 0 2
/dev/mapper/system-files /files ext4 defaults 0 2
/dev/mapper/data-home /home  ext4 defaults 0 2
/dev/system/swap  none swap sw 0 0
```

I had added this line to mount the external USB drive, but removed it.

```
UUID="e29ac408-fd13-415a-92f3-01db5972394e" /louise.bak ext4 defaults 0 2
```

---

### Post by TheFu on 2020-06-03
"defaults" options don't like it when a disk that is in the fstab isn't available.  There's an option - "nofail" which might help.  Also, is /louise.bak an empty directory that already exists?  

Is "/dec/sda" above a typo?
>  The drive in question - /dec/sda is not referenced in the fstab.

Unrelated, but I use lines like this for critical files:
```
/dev/hadar-vg/root        /     ext4    noatime,errors=remount-ro 0  1
```
This way, if the file system as inconsistencies, the mount subsystem will remount read-only to protect the files. That gives anyone on the system a clear indication that something is wrong and needs to be handled.  Someday, it would be nice if that happened, then fsck would be run for native Linux file systems once, the mount attempted again, and continue.  The trick is to only run the fsck once as an automatic thing and not to get into an fsck loop forever.

---

### Post by rsteinmetz70112 on 2020-06-05
> **TheFu said:**
> "defaults" options don't like it when a disk that is in the fstab isn't available.  

The disk was connected, disconnecting the drive allowed the boot to continue. I suppose it might not have been ready on boot. I'll try the nofail option.

> There's an option - "nofail" which might help.  Also, is /louise.bak an empty directory that already exists?  

Yup it's an empty directory specifically to mount the external USB drive.

> Is "/dec/sda" above a typo?

Yup I corrected my post above.

[QUOTE]Unrelated, but I use lines like this for critical files:
```
/dev/hadar-vg/root        /     ext4    noatime,errors=remount-ro 0  1
```
This way, if the file system as inconsistencies, the mount subsystem will remount read-only to protect the files. That gives anyone on the system a clear indication that something is wrong and needs to be handled.  Someday, it would be nice if that happened, then fsck would be run for native Linux file systems once, the mount attempted again, and continue.  The trick is to only run the fsck once as an automatic thing and not to get into an fsck loop forever.

---

