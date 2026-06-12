---
title: "problem installing SDK"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by aksh on 2009-04-16
hi guys please help me out
 i m working on a project 
and trying to install its sdk but getting this problem
i m using ubuntu 8.10

/usr/include/V91SDK exists...
/root/V91SDK exists...
/root/V91SDK/samples exists...
/root/V91SDK/config exists...
/root/V91SDK/Documentation exists...
/root/V91SDK/object exists...
error: Failed dependencies:
	ld-linux.so.2 is needed by arm-linux-binutils-2.10-1.i386
	libc.so.6 is needed by arm-linux-binutils-2.10-1.i386
	libc.so.6(GLIBC_2.0) is needed by arm-linux-binutils-2.10-1.i386
	libc.so.6(GLIBC_2.1) is needed by arm-linux-binutils-2.10-1.i386
error: Failed dependencies:
	/bin/sh is needed by arm-linux-glibc-2.1.3-2.i386
	/usr/bin/perl is needed by arm-linux-glibc-2.1.3-2.i386
error: Failed dependencies:
	arm-linux-binutils is needed by arm-linux-gcc-2.95.2-2.i386
	arm-linux-glibc is needed by arm-linux-gcc-2.95.2-2.i386
	ld-linux.so.2 is needed by arm-linux-gcc-2.95.2-2.i386
	libc.so.6 is needed by arm-linux-gcc-2.95.2-2.i386
	libc.so.6(GLIBC_2.0) is needed by arm-linux-gcc-2.95.2-2.i386
	libc.so.6(GLIBC_2.1) is needed by arm-linux-gcc-2.95.2-2.i386
INSTALL.sh: 70: download/INSTALL.sh: Permission denied
export: 79: /usr/local/arm-linux/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin: bad variable name
 

after so much googlling i m not getting any solution..............

---

### Post by aksh on 2009-04-16
please guys help me
where can i find the latest toolchain
or GLIBC_2.0 and GLIBC_2.1

please help............

---

### Post by aksh on 2009-04-21
hi 
i sorted out the problem  
the problem is with my install file 
the rpm packages i was using was for redhat based linux 
and i have ubuntu thats debian based linux 
so changed the rpm packages with alien 
and worked fine with me 

hope will help u all 
thnx for help.....;):D:popcorn:

---

### Post by keerth516 on 2011-04-06
Hi aksh,

 thanks a lot !!! i tired ur suggestion by converting rpm to deb files using alien ...even though am getting the same error.right now am using ubuntu 8.08 LTS.i am also doing the same project that u have done.please help me out .I am novice in linux, still learning.please let me know what and all u have done in ur project..some how it would help me.

thanks in advance!!!

keerth516.

---

