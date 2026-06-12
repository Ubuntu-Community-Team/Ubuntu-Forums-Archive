---
title: "CDROM not recognized in 10.10 (64 bit)"
date: 2011-02-24
forum: Hardware
---

### Post by gias on 2011-02-24
Hi Ubuntu Users, 

I have been using Ubuntu for a while. After upgrading to 10.10, I was able to use my CD/DVD RW drive without any problem. However, for the last one month, Ubuntu cannot detect the drive. I can manually open the drive, and it seems like doing fine, but Ubuntu cannot recognize it. Here are some log information I went through,

```

root@user:/dev# more /etc/fstab
# swap was on /dev/sda5 during installation
UUID=8a546d6b-26be-4287-9b31-03c2c01df66a none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```
```

root@user:/dev# mount /media/cdrom0
mount: special device /dev/scd0 does not exist

```
```

root@user:/dev# ls -l /dev/cdrom0
ls: cannot access /dev/cdrom0: No such file or directory

```
```

root@user:/dev# ls sd
sda   sda1  sda2  sda5  sdb   sdb1 

```

Your expert help will be welcomed. I have searched this forum extensively for this topic, but could not found any suitable solution.

Thanks.

---

