---
title: "module-assistant and acerhk"
date: 2011-01-07
forum: Hardware
---

### Post by magowiz82 on 2011-01-07
Hi,
I installed module-assistant and acerhk-sources and I'm going to compile and install acerhk module, the problem is that m-a hangs at stage1 at 0%, in my system I've got  build-essentials and linux-source installed.

I tried using this command : 
```
sudo m-a -vt a-i acerhk
```
and the output is :
```
Updating info about acerhk-source

Updated infos about 1 packages
Getting source for kernel version: 2.6.35-24-generic
Kernel headers available in /usr/src/linux
Creating symlink...
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
unpack 
Extracting the package tarball, /usr/src/acerhk.tar.bz2, please wait...
 action tar --bzip2 -x -f /usr/src/acerhk.tar.bz2
 tar --bzip2 -x -f /usr/src/acerhk.tar.bz2
"/usr/share/modass/packages/default.sh" build KVERS=2.6.35-24-generic KSRC=/usr/src/linux-headers-2.6.35-24-generic KDREV=2.6.35-24.42 kdist_image
 debian/rules kdist_clean
/usr/bin/make clean

```

so it hangs at make clean.

What should it be?

---

### Post by crackedboy on 2013-02-09
Have you solved this problem?

---

