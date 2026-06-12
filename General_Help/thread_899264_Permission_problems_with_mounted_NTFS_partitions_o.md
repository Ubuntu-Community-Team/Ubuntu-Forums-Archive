---
title: "Permission problems with mounted NTFS partitions on dual-boot"
date: 2008-08-24
forum: General Help
---

### Post by jrdecastro on 2008-08-24
I have a triple boot system with Ubuntu 8.04, Windows XP 32, and XP 64, and mounted three RAID1 NTFS partitions so I can access them from Ubuntu (by including them in /etc/fstab)
The three directories are XP32C (the XP C:drive), XP32Data (the XP D: drive) and XP64 (the XP 64 bit home drive). All three are NTFS, and Ubuntu lives in a separate, non RAID disk formatted with ext3.

The problem is with permissions. Ubuntu seems to set none for the Windows directories. I can access the Windows directories from my account (which has administrative privileges), but also if I log on from a guest account which has no privileges of any kind. How do I protect these directories so that only my account (or one with administrative privileges, and certainly not the guest account) can mess with them?

If I right-click on any of the mounted NTFS drives, say XP32C, from Nautilus and select "properties" then "permissions" it says "the permissions of "XP32C" could not be determined".

This behaviour seems more than a bit unsafe - is there any way to fix it and have Linux apply some sort of permissions to the mounted NTFS partitions?

Thanks!

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=40fa1aac-1681-4690-9b3b-6209d795da71 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=ccc25a40-e40e-41cc-a37a-d24a1b6c6135 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdd        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/isw_dfcgijeijg_Volume0:11        /media/XP32C  ntfs defaults 0       0
/dev/mapper/isw_dfcgijeijg_Volume0:15        /media/XP32Data  ntfs defaults 0       0
/dev/mapper/isw_dfcgijeijg_Volume0:16        /media/XP64  ntfs defaults 0       0


cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/disk/by-uuid/40fa1aac-1681-4690-9b3b-6209d795da71 / ext3 rw,relatime,errors=remount-ro,data=ordered 0 0
/dev/disk/by-uuid/40fa1aac-1681-4690-9b3b-6209d795da71 /dev/.static/dev ext3 rw,relatime,errors=remount-ro,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.24-19-generic/volatile tmpfs rw,relatime 0 0
tmpfs /dev/shm tmpfs rw,relatime 0 0
devpts /dev/pts devpts rw,relatime 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/mapper/isw_dfcgijeijg_Volume0:11 /media/XP32C fuseblk rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other 0 0
/dev/mapper/isw_dfcgijeijg_Volume0:15 /media/XP32Data fuseblk rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other 0 0
/dev/mapper/isw_dfcgijeijg_Volume0:16 /media/XP64 fuseblk rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other 0 0
securityfs /sys/kernel/security securityfs rw,relatime 0 0
gvfs-fuse-daemon /home/jrc/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1000,group_id=1000 0 0

---

### Post by HalPomeranz on 2008-08-24
You want to use the uid, gid, and umask options like so:

```

/dev/mapper/isw_dfcgijeijg_Volume0:11 /media/XP32C ntfs defaults,umask=007,uid=1000,gid=1000 0 0
/dev/mapper/isw_dfcgijeijg_Volume0:15 /media/XP32Data ntfs defaults,umask=007,uid=1000,gid=1000 0 0
/dev/mapper/isw_dfcgijeijg_Volume0:16 /media/XP64 ntfs defaults,umask=007,uid=1000,gid=1000 0 0

```

Use if your account is not UID/GID 1000 on your system, then change the values above as appropriate.

The upshot of these settings is that the files in the NTFS volumes will be owned by your account and the permissions on the files will be set so that only your UID/GID has access to them.

---

### Post by jrdecastro on 2008-08-24
Thanks - that solved it !
Had to tweak it a bit as some of the permissions in "defaults" conflicted, but it got me there. I removed "defaults" and added the options from "defaults I wanted to keep

---

