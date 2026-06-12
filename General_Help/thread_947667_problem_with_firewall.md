---
title: "problem with firewall"
date: 2008-10-14
forum: General Help
---

### Post by pc_doc on 2008-10-14
I'am having a problem using ufw firewall when i try to check status this is wat i get.
->sudo ufw status
[sudo] password for alan-deb: 
ERROR: uid is 0 but '/' is owned by 1002

What does that mean?

---

### Post by geirha on 2008-10-14
It is saying root has uid 0 (which it must have), but / is owned by a different user.

/ really must be owned by root, and only be writable to root. if / is owned by the user with uid 1002, then that user has potentially access to every single file on the computer, and that's not very secure.

Is it really not owned by root?
```
ls -ld /
ls -ldn /
```

---

### Post by pc_doc on 2008-10-15
> **geirha said:**
> It is saying root has uid 0 (which it must have), but / is owned by a different user.

/ really must be owned by root, and only be writable to root. if / is owned by the user with uid 1002, then that user has potentially access to every single file on the computer, and that's not very secure.

Is it really not owned by root?
```
ls -ld /
ls -ldn /
```

Thanks geirha i will look when i get home from work.

---

### Post by pc_doc on 2008-10-15
> **pc_doc said:**
> Thanks geirha i will look when i get home from work.

Ok this is what i get from the above 


->ls ld /
ls: cannot access ld: No such file or directory
/:
total 92
drwxr-xr-x   2 root root  4096 2008-08-08 17:59 bin/
drwxr-xr-x   3 root root  4096 2008-08-27 18:52 boot/
lrwxrwxrwx   1 root root    11 2008-06-01 08:17 cdrom -> media/cdrom/
drwxr-xr-x  13 root root 14440 2008-10-15 16:54 dev/
drwxr-xr-x 137 root root 12288 2008-10-15 17:06 etc/
drwxr-xr-x   8 root root  4096 2008-08-06 21:40 home/
drwxr-xr-x   2 root root  4096 2008-04-22 18:48 initrd/
lrwxrwxrwx   1 root root    33 2008-06-17 19:06 initrd.img -> boot/initrd.img-2.6.24-19-generic
lrwxrwxrwx   1 root root    33 2008-06-05 19:06 initrd.img.old -> boot/initrd.img-2.6.24-18-generic
drwxr-xr-x  17 root root 12288 2008-09-27 09:55 lib/
drwx------   2 root root 16384 2008-06-01 08:16 lost+found/
drwxr-xr-x   5 root root  4096 2008-10-15 16:54 media/
drwxr-xr-x   2 root root  4096 2008-04-15 06:53 mnt/
drwxr-xr-x   2 root root  4096 2008-04-22 18:48 opt/
dr-xr-xr-x 118 root root     0 2008-10-15 16:53 proc/
drwxr-xr-x  24 root root  4096 2008-10-05 12:00 root/
drwxr-xr-x   2 root root  4096 2008-09-27 09:55 sbin/
drwxr-xr-x   2 root root  4096 2008-04-22 18:48 srv/
drwxr-xr-x  12 root root     0 2008-10-15 16:53 sys/
drwxrwxrwt  14 root root  4096 2008-10-15 17:06 tmp/
drwxr-xr-x  11 root root  4096 2008-06-06 20:05 usr/
drwxr-xr-x  15 root root  4096 2008-04-22 19:07 var/
lrwxrwxrwx   1 root root    30 2008-06-17 19:06 vmlinuz -> boot/vmlinuz-2.6.24-19-generic
lrwxrwxrwx   1 root root    30 2008-06-05 19:06 vmlinuz.old -> boot/vmlinuz-2.6.24-18-generic

->ls -ldn /
drwxr-xr-x 22 1002 100 4096 2008-08-16 09:16 //

does this look ok.

---

### Post by pc_doc on 2008-10-15
> **pc_doc said:**
> Ok this is what i get from the above 


->ls ld /
ls: cannot access ld: No such file or directory
/:
total 92
drwxr-xr-x   2 root root  4096 2008-08-08 17:59 bin/
drwxr-xr-x   3 root root  4096 2008-08-27 18:52 boot/
lrwxrwxrwx   1 root root    11 2008-06-01 08:17 cdrom -> media/cdrom/
drwxr-xr-x  13 root root 14440 2008-10-15 16:54 dev/
drwxr-xr-x 137 root root 12288 2008-10-15 17:06 etc/
drwxr-xr-x   8 root root  4096 2008-08-06 21:40 home/
drwxr-xr-x   2 root root  4096 2008-04-22 18:48 initrd/
lrwxrwxrwx   1 root root    33 2008-06-17 19:06 initrd.img -> boot/initrd.img-2.6.24-19-generic
lrwxrwxrwx   1 root root    33 2008-06-05 19:06 initrd.img.old -> boot/initrd.img-2.6.24-18-generic
drwxr-xr-x  17 root root 12288 2008-09-27 09:55 lib/
drwx------   2 root root 16384 2008-06-01 08:16 lost+found/
drwxr-xr-x   5 root root  4096 2008-10-15 16:54 media/
drwxr-xr-x   2 root root  4096 2008-04-15 06:53 mnt/
drwxr-xr-x   2 root root  4096 2008-04-22 18:48 opt/
dr-xr-xr-x 118 root root     0 2008-10-15 16:53 proc/
drwxr-xr-x  24 root root  4096 2008-10-05 12:00 root/
drwxr-xr-x   2 root root  4096 2008-09-27 09:55 sbin/
drwxr-xr-x   2 root root  4096 2008-04-22 18:48 srv/
drwxr-xr-x  12 root root     0 2008-10-15 16:53 sys/
drwxrwxrwt  14 root root  4096 2008-10-15 17:06 tmp/
drwxr-xr-x  11 root root  4096 2008-06-06 20:05 usr/
drwxr-xr-x  15 root root  4096 2008-04-22 19:07 var/
lrwxrwxrwx   1 root root    30 2008-06-17 19:06 vmlinuz -> boot/vmlinuz-2.6.24-19-generic
lrwxrwxrwx   1 root root    30 2008-06-05 19:06 vmlinuz.old -> boot/vmlinuz-2.6.24-18-generic

->ls -ldn /
drwxr-xr-x 22 1002 100 4096 2008-08-16 09:16 //

does this look ok.

sorry that should of been
ls -ld /
drwxr-xr-x 22 helen-deb users 4096 2008-08-16 09:16 //
ls ldn /
drwxr-xr-x 22 1002 100 4096 2008-08-16 09:16 //

this does not look right as iam the first user on this system and i am in admin group  the user helen-deb is not in admin group.What have i done wrong here.

---

### Post by geirha on 2008-10-15
Seems you forgot the minus/dash (-) on that first ls, but no matter. Seems only / is not owned by root, everything else in / has proper ownership and permission. That means no recursive chown on / has been done, and that's a good thing. You need to change the ownership of / though.
```
sudo chown root:root /
```
Should do the trick.

---

### Post by pc_doc on 2008-10-15
> **geirha said:**
> Seems you forgot the minus/dash (-) on that first ls, but no matter. Seems only / is not owned by root, everything else in / has proper ownership and permission. That means no recursive chown on / has been done, and that's a good thing. You need to change the ownership of / though.
```
sudo chown root:root /
```
Should do the trick.

Thank you geirha that has done the trick i get this now
sudo ufw status
[sudo] password for alan-deb: 
Firewall not loaded
thanks again

---

