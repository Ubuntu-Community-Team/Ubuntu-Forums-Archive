---
title: "Editing fstab"
date: 2008-11-10
forum: General Help
---

### Post by t4ggs on 2008-11-10
I want to be able to write on the ntfs partitions...what should i change in fstab???

```
proc            /proc           proc    defaults        0       0
UUID=4c2e1496-7b3c-47ff-b8b3-0a8ba67628cd /               ext3    relatime,errors=remount-ro 0       1
UUID=1c1187be-42e6-466d-91bb-04a163eb5670 /home           ext3    relatime        0       2
UUID=a03d762d-e6c4-4f0a-b28f-6ca1d9b650fa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=2DAD34E22227FDBC /media/Cruci	ntfs    umask=0222      0       0

UUID=C53008BF82A12446 /media/Data	ntfs    umask=0222      0       0

UUID=1278B11378B0F717 /media/WindowsHD		ntfs    umask=0222      0       0
```

---

### Post by geirha on 2008-11-10
Which release are you using? Dapper, Gutsy, Hardy or Intrepid?

If it's one of the latter three, you should have the ntfs-3g driver already installed, so change fs-type from ntfs to ntfs-3g, and change the options from umask=0222 to defaults,uid=*yourusername*,gid=admin,fmask=113,dmask=002
E.g. (replace *yourusername* with your username):
```
UUID=1278B11378B0F717 /media/WindowsHD ntfs-3g defaults,uid=*yourusername*,gid=admin,fmask=113,dmask=002 0 0
```

This will give your user (uid=yourusername) and the members of the admin group (gid=admin) read and write access, while everyone else will only get read access.

---

### Post by t4ggs on 2008-11-10
thank u

---

