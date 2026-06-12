---
title: "Mangos on ubuntu server x64"
date: 2008-11-24
forum: General Help
---

### Post by JLChafardet on 2008-11-24
Hello dear comunity, im here today to ask if someone has ever had this same problem, or may know how to solve, or even give me some insight on which road to take.

Im installing mangos on an ubuntu server x64, and the configuration line is giving me a problem (for hours now)

the error i get is listed now:

> 
root@KM23712:/usr/mangosSVN# autoreconf --install --force
.ibtoolize: AC_CONFIG_MACRO_DIR([m4]) conflicts with ACLOCAL_AMFLAGS=-I m4
autoreconf: libtoolize failed with exit status: 1
root@KM23712:/usr/mangosSVN#


All the required software is installed on the box, and the versions are as follows:
Make: GNU Make 3.81
automake: automake (GNU automake) 1.10.1
autoconf: autoconf (GNU Autoconf) 2.61
cgg: gcc (Ubuntu 4.3.2-1ubuntu11) 4.3.2
glibc and glibc-dev: libc6
make: GNU Make 3.81
mysql-server: mysql  Ver 14.12 Distrib 5.0.67, for debian-linux-gnu (x86_64) using readline 5.2
libmysql++-dev: installed
libtool: ltmain.sh (GNU libtool) 2.2.4
openssl: libssl-dev (installed)
svn: svn, version 1.5.1 (r32289)
git: git version 1.5.6.3
zlibc: zlibc_0.9k-3_amd64.deb

I have spent over 4 hours trying to fix the problem without any luck.

all help from you if possible is greatly appreciated.

Regards,

---

