---
title: "john the ripper troubles"
date: 2008-07-31
forum: General Help
---

### Post by xGutsAndGloryx on 2008-07-31
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo useradd testuser
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo passwd testuser
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo unshadow /etc/passwd /etc/shadow > mypasswd
xgutsandgloryx@xgutsandgloryx-laptop:~$ sudo john mypasswd
Loaded 3 passwords with 3 different salts (FreeBSD MD5 [32/32])
Crash recovery file is locked: restore
xgutsandgloryx@xgutsandgloryx-laptop:~$ 


how do i fix this problem?

---

### Post by cariboo on 2008-08-01
What do you want to fix? Can you still log in? Do you want to unlock the restore file? More info please?

Jim

---

### Post by xGutsAndGloryx on 2008-08-01
yes how do i unlock the restore file?

---

