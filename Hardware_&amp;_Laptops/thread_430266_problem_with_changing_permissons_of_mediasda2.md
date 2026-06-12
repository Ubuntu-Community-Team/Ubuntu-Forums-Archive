---
title: "problem with changing permissons of /media/sda2"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by harithski on 2007-05-02
Hi,

I have a dell inspiron 6400. I am using Dualboot with windows and kubuntu edgy.
My windows drive is mounted on /media/sda2. 
> 
podolski@eucalyptus:~$ ls -l /media/
total 20
lrwxrwxrwx  1 root root       6 2007-05-01 03:18 cdrom -> cdrom0
drwxr-xr-x  2 root root    4096 2007-05-01 03:18 cdrom0
drwxr-xr-x  2 root root    4096 2007-05-01 03:18 sda1
dr-x------  1 root root    8192 2007-05-01 16:58 sda2
drwxrwx--- 10 root plugdev 4096 1970-01-01 05:30 sda3


My /media/sda2 is  accessible only to root.
can't I make it accessible to my "normal user"

I tried sudo chmod 644 /media/sda2/

> 

podolski@eucalyptus:~$ sudo chmod 644 /media/sda2/
chmod: changing permissions of `/media/sda2/': Read-only file system
podolski@eucalyptus:~$ ls -l /media/
total 20
lrwxrwxrwx  1 root root       6 2007-05-01 03:18 cdrom -> cdrom0
drwxr-xr-x  2 root root    4096 2007-05-01 03:18 cdrom0
drwxr-xr-x  2 root root    4096 2007-05-01 03:18 sda1
dr-x------  1 root root    8192 2007-05-01 16:58 sda2
drwxrwx--- 10 root plugdev 4096 1970-01-01 05:30 sda3



After the installation, it worked fine. But after I logged out for the first time and logged in again it has been this way.

Please help me in making the drive accsessible to my normal login

---

