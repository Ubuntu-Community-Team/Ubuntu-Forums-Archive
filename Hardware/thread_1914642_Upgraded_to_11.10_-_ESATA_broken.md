---
title: "Upgraded to 11.10 - ESATA broken"
date: 2012-01-24
forum: Hardware
---

### Post by captainron042 on 2012-01-24
have an external HDD that I use daily. After finding the time to upgrade to 11.10, I find that my HDD connected through ESATA will not come up.

It works fine with USB.
Going to /media shows my usb HDD, but not the one connected through ESATA, as it did with the previous version.

I started it up with the HDD connected and on, no workie. I tried turning the HDD on while computer was booted, no workie. 

I'm not a hugely advanced ubuntuer, so please be gentle. Thanks

---

### Post by captainron042 on 2012-01-24
This might be handy if anyone wants to take a look at it. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=8360910f-2eee-4129-b47b-734eeca24871 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=a2c07d33-7f79-4afc-bc86-edb0f6a4962e none            swap    sw              0       0
/dev/sda2       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

---

### Post by captainron042 on 2012-01-24
My HDD that I'm having a problem with is called FANTOM1. 

/media/FANTOM1 <- usually connected via ESATA
/media/FANTOM2 <- usually connected via USB

Since I don't see either of these names in FSTAB, I'm confused.

---

### Post by captainron042 on 2012-01-24
OK, but one of them IS under MTAB.



/dev/sda3 / ext3 rw,relatime,errors=remount-ro,commit=0 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
gvfs-fuse-daemon /home/george/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=george 0 0
/dev/sdd1 /media/FANTOM2 ext4 rw,nosuid,nodev,uhelper=udisks 0 0

---

### Post by captainron042 on 2012-01-24
SON OF A GUN!
 
I got sidetracked and started messing with unity in compizconfig and told it to show drives always, and it showed up on the side. When I clicked it, it mounted! 

Now to get it to mount automatically....

---

