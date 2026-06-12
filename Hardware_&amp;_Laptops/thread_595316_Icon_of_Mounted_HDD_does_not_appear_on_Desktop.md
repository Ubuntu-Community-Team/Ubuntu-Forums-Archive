---
title: "Icon of Mounted HDD does not appear on Desktop"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by rpascual on 2007-10-28
Hi,
I made a clean install of Ubuntu 7.04. My system has 3 drives /sda contains the O/S, /sdb has all the data and /sdc has my experimental Ubuntu 7.10

My problem is in mounting /sdb1 - It does not show an icon in my desktop. When I mount /sdc1 I get the icon. I know that /sdb1 is mounted because I can see the data in /media/u01 where I mounted it.

I have a similar PC running Ubuntu 7.10. The difference I can see is that in /media I can see a file .hal-mtab while the PC I'm having problem with has .hal-mtab-lock. I don't know what these files are for but they are empty on both cases.

Here is my fstab entry :
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /media/u01    ext3 defaults 0 2

Any help on this matter will be greatly appreciated.

---

### Post by rpascual on 2007-10-29
Ignore this post. I re-booted my server and the icon came-up.

---

