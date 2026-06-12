---
title: "STrange Permissions issue"
date: 2008-07-27
forum: General Help
---

### Post by onesojourner on 2008-07-27
I am trying to change the permissions on a second drive I have in my computer. I seem to be able to open files, write to files ect. but no one can access the drive via smb. The drive is sdb1 on my fstab below. When I try to use the gui to change the permission it changes them right back. 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=117e675b-b852-4b2b-b02d-3bb3baafd1ac /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=012aa80f-eb5e-4e78-a66b-01d725037f38 /storage        ext3    relatime        0       2
# /dev/sdb1
UUID=7618DAF118DAAF7D /storage2       ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=F8147EE1147EA274 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=4bd12fb5-ef0f-4b9a-a2af-0ded787046e2 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda4 /media/storage ext3 defaults 0 0
/dev/sdb1 /media/storage2 ext3 defaults 0 0
/dev/sda2 /media/windows ntfs defaults 0 0
```







[IMG]http://i291.photobucket.com/albums/ll311/onesojourner/Screenshot-1-1.png[/IMG]

---

### Post by ryanhaigh on 2008-07-28
I had a similar problem and while its been some time I believe the solution was to modify the permissions of the mount directory WITHOUT the drive mounted at the time.

```

sudo umount /storage2
sudo chmod a+rwx /storage2 #change as desired
sudo mount -a

```

---

