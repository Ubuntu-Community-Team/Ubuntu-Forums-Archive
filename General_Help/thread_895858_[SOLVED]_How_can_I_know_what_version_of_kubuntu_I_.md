---
title: "[SOLVED] How can I know what version of kubuntu I am using?"
date: 2008-08-20
forum: General Help
---

### Post by firsttimeuser on 2008-08-20
I think I am using kubuntu 7.0.x, but why the output of "uname -a" and "dmesg" tell me I am using 2.6.24-21?

Thanks!

$ uname -a
Linux noname 2.6.24-21-generic #1 SMP Tue Aug 12 13:37:22 UTC 2008 i686 GNU/Linux

$ dmesg  | grep -i ubuntu
[    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Aug 12 13:37:22 UTC 2008 (Ubuntu 2.6.24-21.40-generic)

---

### Post by eriqjaffe on 2008-08-20
That's telling you which version of the Linux kernel you're running.

```
cat /etc/issue
```

should give you the info you're looking for.

---

### Post by forger on 2008-08-20
This can show you the exact version of the package you use:
```
apt-cache policy kdesktop gnome-about
```
(of course, you have to have installed the kde/gnome package installed through apt or .deb packages)

Mine returns (I have Ubuntu with GNOME):
> 
kdesktop:
  Installed: (none)
  Candidate: 4:3.5.9-0ubuntu7.3
  Version table:
     4:3.5.9-0ubuntu7.3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
     4:3.5.9-0ubuntu7 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
gnome-about:
  Installed: 1:2.22.3-0ubuntu1
  Candidate: 1:2.22.3-0ubuntu1
  Version table:
 *** 1:2.22.3-0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
        100 /var/lib/dpkg/status
     1:2.22.1-0ubuntu6 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages


---

### Post by firsttimeuser on 2008-08-20
thanks man, I am still using solaris command, :)

---

### Post by linuxed on 2008-08-20
One other way to get the ubuntu version is to type the following.

lsb_release -a

Unfortunately for Kubuntu users it's going to display Ubuntu as the distribution, but at least the version is correct.

---

