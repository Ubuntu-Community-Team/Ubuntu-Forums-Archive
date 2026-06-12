---
title: "NTFS detected as linux_raid_member ?"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by khughitt on 2007-10-19
Heya,

I am trying to set-up an NTFS partition to be mounted at boot in fstab, however the only way I am able to mount it is via the /dev/ path, which changes from boot to boot. The partition mounts and works fine though if I explicitly specify the /dev path.

When I try to mount it by UUID however it refuses to mount:

> ubuntu-desktop:~$ sudo mount -a
Failed to access '/dev/disk/by-uuid/adaee235:f652c619:0a8b1215:12320114': No such file or directory


The UUID is different from other NTFS UUIDs, and this is because it is not in fact detected as an NTFS partition by vol_id:

>  sudo /sbin/vol_id /dev/sdc2
ID_FS_USAGE=raid
ID_FS_TYPE=linux_raid_member
ID_FS_VERSION=0.90.0
ID_FS_UUID=adaee235:f652c619:0a8b1215:12320114
ID_FS_UUID_ENC=adaee235:f652c619:0a8b1215:12320114
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=


Anyone have any ideas how I can fix this? Any advice would be much appreciated :)

Thanks!

---

### Post by khughitt on 2007-10-31
*bump*

Suggestions, anyone?

---

### Post by jbernardo on 2007-11-04
I'm also seeing this - but on a ext2 partition, that gets detected as raid:
```
$ sudo vol_id /dev/sdb1
ID_FS_USAGE=raid
ID_FS_TYPE=linux_raid_member
ID_FS_VERSION=0.90.3
ID_FS_UUID=fa9d6872:f3d31f39:ebf526b7:5a59e5e8
ID_FS_UUID_ENC=fa9d6872:f3d31f39:ebf526b7:5a59e5e8
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
```And I can find anything related, except some guys with the same kind of problems in fedora.

I've since gave up, so I backed up the data, and recreated the fs with mkfs.ext3 - and now I have "normal" settings in vol_id:
```
$ sudo vol_id /dev/sdb1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=38528ee9-2f9e-46e0-ba06-151f076d0491
ID_FS_UUID_ENC=38528ee9-2f9e-46e0-ba06-151f076d0491
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
```

---

