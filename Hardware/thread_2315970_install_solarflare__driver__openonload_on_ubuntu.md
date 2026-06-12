---
title: "install solarflare  driver  openonload on ubuntu"
date: 2016-03-04
forum: Hardware
---

### Post by lihui_cui_ on 2016-03-04
I see error information about installing solarflare  driver on ubuntu.

root@office:~/openonload-201509-u1/scripts# ./onload_install 
onload_install: Building OpenOnload.
mmake: Cannot find a make command.  Please define MMAKE_MAKE.
mmakebuildtree: mmake buildtree MMAKEBUILDTREE=1 FAILED
onload_build: FAILED: mmakebuildtree --driver -d x86_64_linux-4.2.0-27-generic
onload_install: ERROR: Build failed.  Not installing.

so i install x86_64_linux-4.2.0-27-generic

root@office:~/openonload-201509-u1/scripts# apt-get install linux-image-4.2.0-27-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-4.2.0-27-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

i find install linux-image-4.2.0-27-generic directory , the file is already installed.

root@office:/lib/modules# ll
total 16
drwxr-xr-x  4 root root 4096 Mar  4 00:36 ./
drwxr-xr-x 21 root root 4096 Mar  4 00:19 ../
drwxr-xr-x  5 root root 4096 Feb 25 09:55 4.2.0-27-generic/
drwxr-xr-x  5 root root 4096 Mar  4 00:36 4.2.0-30-generic/
root@office:/lib/modules# cd 4.2.0-
4.2.0-27-generic/ 4.2.0-30-generic/ 
root@office:/lib/modules# cd 4.2.0-27-generic/
root@office:/lib/modules/4.2.0-27-generic# ll
total 4348
drwxr-xr-x  5 root root    4096 Feb 25 09:55 ./
drwxr-xr-x  4 root root    4096 Mar  4 00:36 ../
lrwxrwxrwx  1 root root      39 Jan 22 11:30 build -> /usr/src/linux-headers-4.2.0-27-generic/
drwxr-xr-x  2 root root    4096 Jan 22 11:21 initrd/
drwxr-xr-x 12 root root    4096 Feb 25 09:55 kernel/
-rw-r--r--  1 root root 1019933 Feb 25 09:55 modules.alias
-rw-r--r--  1 root root 1011903 Feb 25 09:55 modules.alias.bin
-rw-r--r--  1 root root    6613 Jan 22 11:18 modules.builtin
-rw-r--r--  1 root root    8469 Feb 25 09:55 modules.builtin.bin
-rw-r--r--  1 root root  455094 Feb 25 09:55 modules.dep
-rw-r--r--  1 root root  653319 Feb 25 09:55 modules.dep.bin
-rw-r--r--  1 root root     263 Feb 25 09:55 modules.devname
-rw-r--r--  1 root root  176162 Jan 22 11:18 modules.order
-rw-r--r--  1 root root     160 Feb 25 09:55 modules.softdep
-rw-r--r--  1 root root  478531 Feb 25 09:55 modules.symbols
-rw-r--r--  1 root root  589483 Feb 25 09:55 modules.symbols.bin
drwxr-xr-x  3 root root    4096 Feb 25 09:54 vdso/

please you help me, thanks!

---

