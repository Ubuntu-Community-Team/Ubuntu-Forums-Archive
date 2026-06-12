---
title: "Trouble installing new hdd"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by joel8520 on 2009-11-01
I bought a new terabyte hdd that i am using externally through a dock. I used terminal to find my disk info so here it is.
>  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdb
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: signature=00074ddf


I have added the following line to the fstab file
> /dev/sdb  /media/storage vfat user,umask=0000 0 0

and i created a folder in media to mount to called storage. I ran the following in terminal to try and mount it and got this error.

> joel-desktop@joel-desktop-desktop:~$ sudo mount /dev/sdb
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so




i appreciate anyones input on how to fix this. I would love to able use my new harddrive.

---

### Post by bashphoenux on 2009-11-01
See if [THIS]("http://ubuntuforums.org/showthread.php?t=283131") helps ?

---

