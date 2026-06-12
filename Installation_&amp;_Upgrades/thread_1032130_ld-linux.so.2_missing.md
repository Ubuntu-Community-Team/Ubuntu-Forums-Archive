---
title: "ld-linux.so.2 missing"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by sankarapandian.s on 2009-01-06
When I install LabVIEW i  getting this problem., how to solve it ??

sankar@sankar:~/Drivers/rpms$ sudo rpm -ivh nimxs-4.0.1-3006.i386.rpm
error: Failed dependencies:
	/bin/sh is needed by nimxs-4.0.1-3006.i386
	ld-linux.so.2 is needed by nimxs-4.0.1-3006.i386
	libc.so.6 is needed by nimxs-4.0.1-3006.i386
	libc.so.6(GLIBC_2.0) is needed by nimxs-4.0.1-3006.i386
	libc.so.6(GLIBC_2.1) is needed by nimxs-4.0.1-3006.i386
	libc.so.6(GLIBC_2.1.3) is needed by nimxs-4.0.1-3006.i386
	libc.so.6(GLIBC_2.2) is needed by nimxs-4.0.1-3006.i386
	libc.so.6(GLIBC_2.2.4) is needed by nimxs-4.0.1-3006.i386
	libdl.so.2 is needed by nimxs-4.0.1-3006.i386
	libdl.so.2(GLIBC_2.0) is needed by nimxs-4.0.1-3006.i386
	libdl.so.2(GLIBC_2.1) is needed by nimxs-4.0.1-3006.i386
	libm.so.6 is needed by nimxs-4.0.1-3006.i386
	libm.so.6(GLIBC_2.0) is needed by nimxs-4.0.1-3006.i386
	libpthread.so.0 is needed by nimxs-4.0.1-3006.i386
	libpthread.so.0(GLIBC_2.0) is needed by nimxs-4.0.1-3006.i386
	libpthread.so.0(GLIBC_2.1) is needed by nimxs-4.0.1-3006.i386
	librt.so.1 is needed by nimxs-4.0.1-3006.i386
	librt.so.1(GLIBC_2.2) is needed by nimxs-4.0.1-3006.i386

please help to solve this.
sankar.s

---

### Post by lemming465 on 2009-01-10
What's the host OS version (cat /etc/lsb-release)?  If it's Ubuntu, which we expect on this forum :-), then the package manager is debian's *dkpg*, not RPM.  If you have an RPM which you need to install, try installing *alien* and using that to convert it to a .deb.  You can then install the result with *dpkg -i*.

---

