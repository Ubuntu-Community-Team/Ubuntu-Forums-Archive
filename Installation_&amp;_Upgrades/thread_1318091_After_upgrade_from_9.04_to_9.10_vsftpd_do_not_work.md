---
title: "After upgrade from 9.04 to 9.10 vsftpd do not work"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by gorvas on 2009-11-07
After upgrading from Ubuntu 9.04 -> 9.10 i have some issues that were present after the upgrade.

1. Samba doesn't start it self have to do it manually (this is a know bug)

2. Mysql didn't start it crashed. Fix is to comment the skip-bdb in /etc/mysql/my.cnf file. Then try to start mysql it should work. 

3. Vsftpd don't work with virtual users. All the users can log in to the FTP but they get a 500 OOPS: child died. Then the connection is closed. 
This is a bug with the 2.2.0 vsftpd in 9.10. Upgrade to vsftpd 2.2.1 and the problem will be fixed.
The issue is about passive addresses if that is disabled in the vsftpd config file then 2.2.0 works fine.
[https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/462749](https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/462749)

---

