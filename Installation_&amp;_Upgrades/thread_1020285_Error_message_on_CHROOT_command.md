---
title: "Error message on CHROOT command"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by wachaca on 2008-12-24
Hello,
I am trying to execute the command
chroot /newinstall
But this gives me the error message 
chroot: cannot run command `/bin/bash': Exec format error

when I execute ls -ld /newinstall I get
drwxr-xr-x  18 root root 1024 May  6  2008 /newinstall/

the command mount shows
/dev/cciss/c0d0p4 on /newinstall type ext2 (rw)

I am on a redhat server trying to follow the steps at:
[http://www.debian.org/releases/stable/amd64/apds03.html.en](http://www.debian.org/releases/stable/amd64/apds03.html.en)

in order to switch from redhat to ubuntu.

Thanks for your help

---

