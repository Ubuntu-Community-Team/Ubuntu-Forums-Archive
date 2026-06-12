---
title: "cant write to fat32 driver"
date: 2009-03-04
forum: Hardware
---

### Post by yusuo85 on 2009-03-04
having trouble writing to my fat32 drive its not letting me no matter what i try

ive tried sudo chown yusuo /media/media2

ive also tried editing my fstab as seen below

       /proc           proc    defaults        0       0
# /dev/sdb1
UUID=3afbea91-c12c-4079-86ff-cc3a9fac5597 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=82b5d9df-c4fb-4bcf-9884-7724b690c935 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb3 /media/media ext3 defaults 0 0
/dev/sda1 /media/media2 rw,auto,umask=000 0 0

if anyone can help it would be appreciated

---

### Post by taurus on 2009-03-04
> **yusuo85 said:**
> having trouble writing to my fat32 drive its not letting me no matter what i try

ive tried sudo chown yusuo /media/media2

ive also tried editing my fstab as seen below

       /proc           proc    defaults        0       0
# /dev/sdb1
UUID=3afbea91-c12c-4079-86ff-cc3a9fac5597 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=82b5d9df-c4fb-4bcf-9884-7724b690c935 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb3 /media/media ext3 defaults 0 0
**[COLOR="Red"]/dev/sda1 /media/media2 rw,auto,umask=000 0 0[/COLOR]**

if anyone can help it would be appreciated

Don't you also need to include the filesystem for an entry in /etc/fstab?

```

/dev/sda1 /media/media2 **[COLOR="Blue"]vfat[/COLOR]** rw,auto,umask=000 0 0

```

---

