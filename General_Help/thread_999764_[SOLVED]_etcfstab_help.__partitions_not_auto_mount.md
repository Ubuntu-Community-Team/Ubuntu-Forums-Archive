---
title: "[SOLVED] /etc/fstab help.  partitions not auto mounting."
date: 2008-12-02
forum: General Help
---

### Post by Fahuadai on 2008-12-02
Hello.

Here is my /etc/fstab entry:

```

proc            /proc           proc    defaults        0       0
UUID=4c408924-f314-4ecf-b176-4d959e166e58 / ext3 relatime,errors=remount-ro 0 1
/dev/sdb1 none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb2 /home/mark/films ext3 rw,exec,auto,user,async,relatime 0 0
/dev/sdb3 /home/mark/series ext3 rw,exec,auto,users,async,relatime 0 0
/dev/sda3 /home ext3 rw,exec,auto,user,async 0 0

```

My root partition and /home partition mount fine, and everything is working as expected.

But the drives mounting to films and series are not. The folders exist, and the owners are mark. I see the drives listed under volumes when i browse in dolphin. i can click them but do not see the data. I know the data is there as i've been playing around and can get them to mount sometimes, but never automatically on login correctly.

I'm using kubuntu 8.10.

Thanks in advance for any advice given.

---

### Post by sisco311 on 2008-12-02
try to change the order of the entries and use the uuid:
> 
*UUID=**uuid-of-sda3** /home ext3 rw,exec,auto,user,async 0 0*
UUID=**uuid-of-sdb2** /home/mark/films ext3 rw,exec,auto,user,async,relatime 0 0
UUID=**uuid-of-sdb3** /home/mark/series ext3 rw,exec,auto,users,async,relatime 0 0


to get the uuid of the partition:
```
sudo vol_id -u /dev/sda3
sudo vol_id -u /dev/sdb2
...
```

---

### Post by taurus on 2008-12-02
The entry for /home should go before the other two entries, /home/mark/films & /home/mark/series, in /etc/fstab.

---

### Post by Fahuadai on 2008-12-02
Thank you both.

The reordering solved the problem. :biggrin:

---

