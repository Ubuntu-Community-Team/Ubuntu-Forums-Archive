---
title: "Installing Intel536ep; ..unkown distribution.."
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by david.holland on 2006-04-09
Trying to install Intel536ep modem driver:
Logged in as root and done both 'make clean' & 'make 536'; no problems,
then I do 'make install' and I get this:

root@ubuntu:~/Intel-536# make install
Try `uname --help' for more information.
rm -f /etc/hamregistry.bin
bash Intel536_inst
running kernel 2.6.12-9-386
installing hamregistry, used for persistant storage
installing Intel536 driver
**unknown distribution. no boot scripts installed**
make: *** [install] Error 1
root@ubuntu:~/Intel-536#

why is the installation not recognising the distro?

Using Ubuntu5.10 on P3 1.0GHz/256MB RAM/20GB Hdd/Swap 400MB

---

### Post by hajk on 2006-04-09
Hmm, you seem to have compiled a driver package on your own... I can think of a whole lot of problems that could happen that way, starting with the version of GCC used: this MUST match the version used to compile the kernel (gcc-3.4). So, at any rate you must make sure that the environment variable CC is set that way:

export CC=gcc-3.4

before you do a compile.

---

