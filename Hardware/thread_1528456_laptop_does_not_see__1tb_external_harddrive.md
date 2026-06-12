---
title: "laptop does not see  1tb external harddrive"
date: 2010-07-10
forum: Hardware
---

### Post by rocker2344 on 2010-07-10
I have done everything i could, even booting into windows. here is a copy and paste of things i have tried

```
user@home:~$ sudo dd of=/dev/ZERO if=/dev/sdb
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.003209 s, 0.0 kB/s
user@home:~$ sudo dd of=/dev/urandom if=/dev/sdb
dd: reading `/dev/sdb': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.0034966 s, 0.0 kB/s
user@home-server:~$ umount /dev/sdb
umount: /dev/sdb is not mounted (according to mtab)
user@home:~$ fdisk /dev/sdb

Unable to open /dev/sdb
user@home:~$ sudo fdisk /dev/sdb

Unable to read /dev/sdb
user@home:~$

```please help, status of reading
ubuntu: S.M.A.R.T. sees it and says it is usable, but i cant do anything (no it is not locked i checked the hardware switch) 
windows makes the something connected noise and that is it.
mac has a heart attack and freezes up.

---

