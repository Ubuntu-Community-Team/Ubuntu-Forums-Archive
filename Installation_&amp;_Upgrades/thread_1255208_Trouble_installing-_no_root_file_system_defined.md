---
title: "Trouble installing- no root file system defined"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by Oddballs on 2009-09-01
I used UNetboot without a flash drive to get it on the computer. now I am stuck installing it. It says:Your installation medium is on /dev/sda2. You will not be able to create, delete, or resize partitions on this disk, but you may be able to install to existing partitions there.

Device      Type   Mount Point      Format?       Size              Used 

/dev/sda
/dev/sda1   fat16                                           73 MB          33MB
/dev/sda2   ntfs                                             76429 MB     Unknown
/dev/sda3   fat32                                           3520 MB      2853 MB


When I click next it says "No root file system is defined.

Please correct this from the partitioning menu." I do not know what to do. I want Ubuntu to be the only OS.

---

### Post by gnuyoga on 2009-09-01
this will be of help
[http://ubuntuforums.org/showthread.php?t=427540&highlight=unetboot](http://ubuntuforums.org/showthread.php?t=427540&highlight=unetboot)

there is a option to specify  formatpartition=yes when starting the script from host.

- sree

---

