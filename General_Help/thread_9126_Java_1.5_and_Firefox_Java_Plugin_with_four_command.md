---
title: "Java 1.5 and Firefox Java Plugin with four commands"
date: 2004-12-24
forum: General Help
---

### Post by macewan on 2004-12-24
[https://www.ubuntulinux.org/wiki/Java15](https://www.ubuntulinux.org/wiki/Java15)

Please let me know if I goofed.

Cheers,
macewan

---

### Post by TopDog on 2004-12-24
wget went fine, but the rest:
> root@ubuntu:/home/gaute # dpkg -i su*.deb
Selecting previously deselected package sun-j2sdk1.5.
(Reading database ... 78516 files and directories currently installed.)
Unpacking sun-j2sdk1.5 (from sun-j2sdk1.5_1.5.0_i386.deb) ...
dpkg: dependency problems prevent configuration of sun-j2sdk1.5:
 sun-j2sdk1.5 depends on sun-j2sdk1.5debian; however:
  Package sun-j2sdk1.5debian is not installed.
dpkg: error processing sun-j2sdk1.5 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-j2sdk1.5
root@ubuntu:/home/gaute # apt-get install sun-j2sdk1.5debian
Reading Package Lists... Done
Building Dependency Tree... Done
Package sun-j2sdk1.5debian is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-j2sdk1.5debian has no installation candidate
root@ubuntu:/home/gaute #


---

### Post by macewan on 2004-12-24
[QUOTE=TopDog]wget went fine, but the rest:[/QUOTE]
 add multiverse to you sources.list

---

