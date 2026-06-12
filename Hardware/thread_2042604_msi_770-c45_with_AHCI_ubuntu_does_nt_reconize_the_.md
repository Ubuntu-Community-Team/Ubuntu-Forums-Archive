---
title: "msi 770-c45 with AHCI ubuntu does nt reconize the hdd"
date: 2012-08-15
forum: Hardware
---

### Post by gabak on 2012-08-15
what can i do?
if i go to disk utility i see the hard drive.
but the installer does nt.
if i use IDE mode it does work but i guess it will work slower.

thxs in advance

---

### Post by gabak on 2012-08-18
ubuntu@ubuntu:~$ df
Filesystem     1K-blocks   Used Available Use% Mounted on
/cow             1030424  85056    945368   9% /
udev             1022792      4   1022788   1% /dev
tmpfs             412172    888    411284   1% /run
/dev/sr0          718124 718124         0 100% /cdrom
/dev/loop0        688256 688256         0 100% /rofs
tmpfs            1030424     24   1030400   1% /tmp
none                5120      0      5120   0% /run/lock
none             1030424    176   1030248   1% /run/shm
ubuntu@ubuntu:~$

---

### Post by gabak on 2012-08-18
in test mode i open a terminal and i type this and now everything works.
:D

ubuntu@ubuntu:~$ sudo apt-get remove dmraid

---

