---
title: "Quota Problems"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by vermax on 2008-12-05
quotacheck: Cannot find filesystem to check or filesystem not mounted with quota option.

I am getting this error when trying to run:

quotacheck -avugm

I have tried rebooting the system, I have edited my fstab to look like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0ecb7f7a-ff44-42ba-b31a-eee4b57b8d16  /  ext3  grpquota,suid,dev,usrquota,relatime,exec  0  1
# /dev/sda5
UUID=7c7eb245-49f0-4332-bf13-82395942fe8e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0



I have done:

root@localhost:touch /quota.user /quota.group
root@localhost:/etc# chmod 600 /quota.*
root@localhost:/etc# mount -o remount /


I can't seem to figure this out to save my life.

Any help is greatly appreciated!

Regards,

Vermax

---

