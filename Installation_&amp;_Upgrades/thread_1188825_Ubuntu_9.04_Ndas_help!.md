---
title: "Ubuntu 9.04 Ndas help!"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by Fuitab on 2009-06-16
Hello, I'm new to Ubuntu and the Unix system and have always used windows. I want to mount my ndas via a router but it wont work.
I followed everything on [http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB](http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB)
Everything pretty much went smoothly and worked fine, I patched the thing with both patches (27, 28)
So, after all that, I registered the ndas with my keys and it worked. I even got the slot number (which was 1).
But what I typed sudo ndasadmin enable -s 1 -o w, the terminal just does nothing. I did this a few times and rebooted a few times as well. 
After some time, I tried doing it agian and it said:
enable: Block device /dev/ndas-00503858-0 is already enabled.
But when I do blkid, the device doesn't show up.
When I run Gparted via the terminal, it writes:
Could not stat device /dev/ndas-00503858-0 - No such file or directory.
So how can I get it to work?
Please help! I have to sleep right now so I'll have to answer tommorrow.

---

### Post by Fuitab on 2009-06-16
No one? Still need help.

---

### Post by Robb987 on 2009-06-17
Hello Fruitap,

I used NDAS on version 8.04. I just did a clean install for 9.04 and I have to go through the NDAS installation too.

Did you have a look in the open and closed tickets on [http://code.ximeta.com/trac-ndas/report/2](http://code.ximeta.com/trac-ndas/report/2) ?

---

### Post by Fuitab on 2009-06-17
When you do that 
```
dpkg-buildpackage -rfakeroot

```

Is it suppose to write out
```

dpkg-deb: building package `ndasadmin' in `../ndasadmin_1.1-24_i386.deb'.
 signfile ndas_1.1-24.dsc
gpg: skipped "Ilgu Hong <ighong@ximeta.com>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

 dpkg-genchanges  >../ndas_1.1-24_i386.changes
dpkg-genchanges: including full source code in upload
dpkg-buildpackage: full upload; Debian-native package (full source is included)
dpkg-buildpackage: warning: Failed to sign .dsc and .changes file

```
at the end?

---

### Post by Robb987 on 2009-06-18
> **Fuitab said:**
> 

```

gpg: skipped "Ilgu Hong <ighong@ximeta.com>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

 dpkg-genchanges  >../ndas_1.1-24_i386.changes
dpkg-genchanges: including full source code in upload
dpkg-buildpackage: full upload; Debian-native package (full source is included)
dpkg-buildpackage: warning: Failed to sign .dsc and .changes file

```
at the end?

It says you didn't sign the package as it can't find gnupg or PGP.

take a look at: [http://www.debian.org/doc/maint-guide/ch-build.en.html](http://www.debian.org/doc/maint-guide/ch-build.en.html) 

I don't think this is an ubuntu related problem so you won't get much help on this forum. A better place will be: [http://code.ximeta.com/trac-ndas/wiki](http://code.ximeta.com/trac-ndas/wiki)

---

### Post by Fuitab on 2009-06-18
Sorry I took to long to respond, my internet has been on the fritz. Thanks for helping me I was looking at the debian complete rebuild guide and I don't know what the "Main directory" is. Sorry, I'm really new to ubuntu I don't really know much yet.

---

### Post by Robb987 on 2009-06-19
Oh, I gave you the link to "debian complete rebuild guide" only for some background information about signing a package, it is not a guide for setting up the NDAS. It is not a problem at all that you don't understand everything. Just read and learn as much as you can.


The "Main directory" is in this case the place where you untarred your universal tarball. if your tarrball is here: /home/fruitab/ndas-1.1-24.tar.gz, and you followed the instructions exactly, your main directory for NDAS will be: "/home/fruitab/ndas-1.1-24".

"/home/fruitab/ndas-1.1-24" is the place to you put your patches too.


I installed the NDAS software too and my program crashes when I apply command: "/usr/sbin/ndasadmin enable -s 1 -o w".

---

