---
title: "cdfs-src problem on 8.04"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by b4r4n on 2009-05-11
```
root@baran-desktop:~# apt-get install cdfs-src
Reading package lists... Done
Building dependency tree
Reading state information... Done
cdfs-src is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 345 not upgraded.
root@baran-desktop:~# mount -t cdfs /dev/sr0 /media/cdrom0/
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@baran-desktop:~# modprobe cdfs
FATAL: Module cdfs not found.
root@baran-desktop:~# mount -t cdfs /dev/sr0 /media/cdrom0/
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@baran-desktop:~# cd modules/cdfs/2.6/
root@baran-desktop:~/modules/cdfs/2.6# make
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/baran/modules/cdfs/2.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/baran/modules/cdfs/2.6/root.o
  CC [M]  /home/baran/modules/cdfs/2.6/audio.o
  CC [M]  /home/baran/modules/cdfs/2.6/cdXA.o
  CC [M]  /home/baran/modules/cdfs/2.6/cddata.o
  CC [M]  /home/baran/modules/cdfs/2.6/hfs.o
  CC [M]  /home/baran/modules/cdfs/2.6/iso.o
  CC [M]  /home/baran/modules/cdfs/2.6/proc.o
  CC [M]  /home/baran/modules/cdfs/2.6/utils.o
  CC [M]  /home/baran/modules/cdfs/2.6/daemon.o
  CC [M]  /home/baran/modules/cdfs/2.6/discid.o
  CC [M]  /home/baran/modules/cdfs/2.6/toc.o
  LD [M]  /home/baran/modules/cdfs/2.6/cdfs.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/baran/modules/cdfs/2.6/cdfs.mod.o
  LD [M]  /home/baran/modules/cdfs/2.6/cdfs.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
root@baran-desktop:~/modules/cdfs/2.6# make install
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/baran/modules/cdfs/2.6 modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  INSTALL /home/baran/modules/cdfs/2.6/cdfs.ko
  DEPMOD  2.6.24-16-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
root@baran-desktop:~/modules/cdfs/2.6# insmod cdfs.ko
root@baran-desktop:~/modules/cdfs/2.6# modprobe cdfs
FATAL: Module cdfs not found.
root@baran-desktop:~/modules/cdfs/2.6# mount -t cdfs /dev/sr0 /media/cdrom0/
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@baran-desktop:~/modules/cdfs/2.6# uname -r
2.6.24-16-generic
root@baran-desktop:~/modules/cdfs/2.6#    
```
how to i can add cdfs module to kernel ?

---

