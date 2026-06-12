---
title: "Second hard drive don't want to auto-mount"
date: 2010-09-24
forum: Hardware
---

### Post by papamike3108 on 2010-09-24
Hi, I installed a new harddrive to my Ubuntu server. Everything is fine, I can mount it manually but the auto mount in the fstab doesn't seems to work. Here is the df info (the second HD is sdb1):


Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext3    74328480   1931712  68650816   3% /
varrun       tmpfs     2073836       172   2073664   1% /var/run
varlock      tmpfs     2073836         0   2073836   0% /var/lock
udev         tmpfs     2073836        56   2073780   1% /dev
devshm       tmpfs     2073836         0   2073836   0% /dev/shm
/dev/sdb1     ext3    15244756    168720  14307732   2% /media/backup

And here is the FSTAB line:


# /dev/sda1
UUID=8feac615-216a-4bf5-8099-c09964bc95db /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=36b4f7bc-ab6f-4b84-afb5-a0aa0faed623 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/backup   ext3    default 0       0


Any ideas?

Thanks

---

### Post by IcarusR on 2010-09-24
> /dev/sdb1 /media/backup ext3 default 0 0

Does mount point exist ?

May be a better idea to mount it somewhere in your user home folder (less chances of permissions problems) ie

```
~/backup
```

Is there any clues in the log files ??

---

