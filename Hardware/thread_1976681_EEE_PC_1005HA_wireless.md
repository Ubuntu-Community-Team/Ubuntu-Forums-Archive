---
title: "EEE PC 1005HA wireless"
date: 2012-05-09
forum: Hardware
---

### Post by H3R3T1K on 2012-05-09
I've already once inquired about  wireless problems with my netbook on ask ubuntu: [http://askubuntu.com/questions/102205/wireless-on-my-eee-1005ha-doesnt-work-properly-yet-theres-no-additional-driver](http://askubuntu.com/questions/102205/wireless-on-my-eee-1005ha-doesnt-work-properly-yet-theres-no-additional-driver)

Wireless still doesn't work after a complete reinstall with Lubuntu 12.04 and I'd like to post the output from the operation mentioned in the answer on ask ubuntu here. There's something wrong with "make". Help would be appreciated!

edit: The hickup during install of "make" happened because I forgot to plug in the patch cable.

```
arno@arno-1005HA:~$ cd /home/arno/Downloads
arno@arno-1005HA:~/Downloads$ dir
compat-wireless-3.4-rc3-1.tar.bz2
arno@arno-1005HA:~/Downloads$ tar -xf compat-wireless-3.4-rc3-1.tar.bz2
arno@arno-1005HA:~/Downloads$ dir
compat-wireless-3.4-rc3-1  compat-wireless-3.4-rc3-1.tar.bz2
arno@arno-1005HA:~/Downloads$ cd compat-wireless-3.4-rc3-1
arno@arno-1005HA:~/Downloads/compat-wireless-3.4-rc3-1$ make
The program 'make' is currently not installed.  You can install it by typing:
sudo apt-get install make
arno@arno-1005HA:~/Downloads/compat-wireless-3.4-rc3-1$ sudo apt-get install make
[sudo] password for arno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  make-doc
The following NEW packages will be installed:
  make
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 116 kB of archives.
After this operation, 319 kB of additional disk space will be used.
Err http://de.archive.ubuntu.com/ubuntu/ precise/main make i386 3.81-8.1ubuntu1
  Temporary failure resolving 'de.archive.ubuntu.com'
Failed to fetch http://de.archive.ubuntu.com/ubuntu/pool/main/m/make-dfsg/make_3.81-8.1ubuntu1_i386.deb  Temporary failure resolving 'de.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
arno@arno-1005HA:~/Downloads/compat-wireless-3.4-rc3-1$ sudo apt-get install make
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  make-doc
The following NEW packages will be installed:
  make
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 116 kB of archives.
After this operation, 319 kB of additional disk space will be used.
Get:1 http://de.archive.ubuntu.com/ubuntu/ precise/main make i386 3.81-8.1ubuntu1 [116 kB]
Fetched 116 kB in 0s (301 kB/s)
Selecting previously unselected package make.
(Reading database ... 127643 files and directories currently installed.)
Unpacking make (from .../make_3.81-8.1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up make (3.81-8.1ubuntu1) ...
arno@arno-1005HA:~/Downloads/compat-wireless-3.4-rc3-1$ make
make[1]: gcc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
make[1]: gcc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
./scripts/gen-compat-autoconf.sh /home/arno/Downloads/compat-wireless-3.4-rc3-1/.config /home/arno/Downloads/compat-wireless-3.4-rc3-1/config.mk > include/linux/compat_autoconf.h
make[1]: gcc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
make[1]: gcc: Command not found
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
make -C /lib/modules/3.2.0-24-generic/build M=/home/arno/Downloads/compat-wireless-3.4-rc3-1 modules
/usr/src/linux-headers-3.2.0-24-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-3.2.0-24-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
/usr/src/linux-headers-3.2.0-24-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
make[2]: gcc: Command not found
make[2]: gcc: Command not found
  CC [M]  /home/arno/Downloads/compat-wireless-3.4-rc3-1/compat/main.o
/bin/sh: 1: gcc: not found
make[3]: *** [/home/arno/Downloads/compat-wireless-3.4-rc3-1/compat/main.o] Error 127
make[2]: *** [/home/arno/Downloads/compat-wireless-3.4-rc3-1/compat] Error 2
make[1]: *** [_module_/home/arno/Downloads/compat-wireless-3.4-rc3-1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
make: *** [modules] Error 2
arno@arno-1005HA:~/Downloads/compat-wireless-3.4-rc3-1$ 

```edit: > Wireless (Atheros AR9285) works out of the box, but connection is flaky. To fix, open a terminal and type 'sudo apt-get install linux-backports-modules-karmic' This didn't work.

---

