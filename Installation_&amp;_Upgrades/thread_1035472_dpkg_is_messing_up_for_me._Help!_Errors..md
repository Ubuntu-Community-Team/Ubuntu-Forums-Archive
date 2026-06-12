---
title: "dpkg is messing up for me. Help! Errors."
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by TheJoke on 2009-01-09
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

Thats the error i get. I tried all that dpkg --configure -a and i put sudo in front of it but it still won't work. Help.

I tried this.

"I googled around and found a possible solution for you. You can try deleting the update that has been downloaded, then run dpkg. So in order you can try (at your own risk, of course)
Code:

sudo rm /var/lib/dpkg/updates/0001
sudo dpkg --reconfigure -a"

Then when it was working again, I would run sudo aptitude update.
After the first part, it shows a bunch of selections. Which one should i pick?

How do i delete/var/lib/dpkg/updates/?

izese@izese-desktop:~$ ls -al /var/lib/dpkg/updates
total 76
drwxr-xr-x 2 root root 4096 2009-01-09 17:02 .
drwxr-xr-x 8 root root 4096 2008-12-17 18:57 ..
-rw-r--r-- 1 root root 1144 2008-12-17 18:57 0000
-rw-r--r-- 1 root root 1143 2008-12-17 18:57 0002
-rw-r--r-- 1 root root 1143 2008-12-17 18:57 0003
-rw-r--r-- 1 root root 1137 2008-12-17 18:57 0004
-rw-r--r-- 1 root root 1130 2008-12-17 18:57 0005
-rw-r--r-- 1 root root 1085 2008-12-17 18:57 0006
-rw-r--r-- 1 root root 1078 2008-12-17 18:57 0007
-rw-r--r-- 1 root root 1084 2008-12-17 18:57 0008
-rw-r--r-- 1 root root 1084 2008-12-17 18:57 0009
-rw-r--r-- 1 root root 1078 2008-12-17 18:57 0010
-rw-r--r-- 1 root root 1071 2008-12-17 18:57 0011
-rw-r--r-- 1 root root 1036 2008-12-17 18:57 0012
-rw-r--r-- 1 root root 1029 2008-12-17 18:57 0013
-rw-r--r-- 1 root root 1035 2008-12-17 18:57 0014
-rw-r--r-- 1 root root 1035 2008-12-17 18:57 0015
-rw-r--r-- 1 root root 1029 2008-12-17 18:57 0016
-rw-r--r-- 1 root root 1022 2008-12-17 18:57 tmp.i


izese@izese-desktop:~$ df -h.
df: invalid option -- '.'
Try `df --help' for more information.
izese@izese-desktop:~$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda6 118G 23G 90G 21% /
tmpfs 441M 0 441M 0% /lib/init/rw
varrun 441M 216K 441M 1% /var/run
varlock 441M 0 441M 0% /var/lock
udev 441M 2.7M 439M 1% /dev
tmpfs 441M 692K 441M 1% /dev/shm
lrm 441M 2.0M 439M 1% /lib/modules/2.6.27-7-generic/volatile

:confused::confused::confused:

---

### Post by TheJoke on 2009-01-09
Help?

---

