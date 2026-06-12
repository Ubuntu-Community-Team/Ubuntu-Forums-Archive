---
title: "fstab DVD HD issue"
date: 2008-10-12
forum: General Help
---

### Post by tranquito on 2008-10-12
Hi there. Just tried to add a new internal DVD drive to my computer which is running ubuntu hardy. 
Add 1 DVD drive. Start machine. I login and notice that my desktop wallpaper doesn't display but ignore it. DVD drive works perfectly. I then start to wonder why my wallpaper didn't show up and notice that my second HD isn't on the desktop. After many case opening and rebooting sessions I open GParted to check if the hd is visible. Sure enough it exists but is not mounted. The path reads /dev/sdb1.

I opened /etc/fstab and tried to add a mount point for it but I got this error:
wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg reads:
  248.605744] ext3: No journal on filesystem on sdb1
[ 1129.354923] ext3: No journal on filesystem on sdb1

fstab reads:
   # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc2
UUID=b4c2a15c-53a2-4991-94a5-92e541b7b4bc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=453948b2-2bbf-46df-8246-e12c456397e0 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1 	/storage 	ext3 	defaults 	    0       0

Please help, I'm completely stumped. Why would adding a DVD drive cause this much hastle?

---

