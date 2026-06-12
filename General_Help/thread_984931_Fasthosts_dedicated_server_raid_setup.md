---
title: "Fasthosts dedicated server raid setup"
date: 2008-11-17
forum: General Help
---

### Post by Adurbe on 2008-11-17
Hello All,

We have recently purchased the server below from fasthosts

[http://www.fasthosts.co.uk/dedicatedservers/ds-650_linux/](http://www.fasthosts.co.uk/dedicatedservers/ds-650_linux/)

I am fairly new to linux as a server OS and am after help in setting up a mirrored raid on this system (6.06lts)

Below is an fdisk of the current (default) partition setup

[I]root@ubuntu:~# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    5  Extended
/dev/sda5               1          62      497952   82  Linux swap / Solaris
/dev/sda6              63         670     4883728+  83  Linux
/dev/sda7             671        1278     4883728+  83  Linux
/dev/sda8            1279       30401   233930466   83  Linux
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    5  Extended[/I]

Re-installing the OS is not an option as the os is done using fasthost provided 'os restore' and I have no facility to boot off a cd/dvd (that im aware of)

Thanks in advance for any help 

Adurbe

---

### Post by jenismith73 on 2010-11-24
Unlimitedgb.com is much beyond my expectations.. I am honestly telling it is best hosting company that i had ever met.

---

### Post by jenismith73 on 2010-11-24
Unlimitedgb.com is much beyond my expectations.. I am honestly telling it is best hosting company that i had ever met.

---

