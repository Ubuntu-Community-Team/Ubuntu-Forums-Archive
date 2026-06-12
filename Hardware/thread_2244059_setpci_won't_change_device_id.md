---
title: "setpci won't change device_id"
date: 2014-09-13
forum: Hardware
---

### Post by lsusb on 2014-09-13
```
[FONT=Consolas][aaa@bbb ~]$ sudo su[/FONT][sudo] password for aaa: 
[root@bbb aaa]# setpci -v -s 01:00.0 DEVICE_ID=11BA
0000:01:00.0 @02 11ba
[root@bbb aaa]# setpci -v -s 01:00.0 DEVICE_ID [FONT=Consolas]0000:01:00.0 @02 = 1180[/FONT]
```

I'm trying to change the DEVICE_ID of my graphic card from "1180" to "11ba". Setpci seems to be applying the change without errors, but when I read the register I just modified it's still the same value as it was before.

---

