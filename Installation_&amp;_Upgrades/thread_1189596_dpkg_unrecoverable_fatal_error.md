---
title: "dpkg unrecoverable fatal error"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by serez on 2009-06-16
hello i have a problem and want to consult for a solution.

i`m using ubuntu 9.04 on an acer 4920g. whenever i want to install a program or software i got this error

```

serez@serez-laptop:~$ sudo apt-get install nfs-kernel-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libevent1 libgssglue1 libnfsidmap2 librpcsecgss3 nfs-common portmap
The following NEW packages will be installed:
  libevent1 libgssglue1 libnfsidmap2 librpcsecgss3 nfs-common
  nfs-kernel-server portmap
0 upgraded, 7 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/514kB of archives.
After this operation, 1597kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package libevent1.
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `winbind' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
serez@serez-laptop:~$ 

```

i got tis error since i want to configure samba with openldp. how to solve this problem? can i revert it back to original state?

---

