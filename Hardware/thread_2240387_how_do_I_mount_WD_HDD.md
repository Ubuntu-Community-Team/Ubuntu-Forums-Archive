---
title: "how do I mount WD HDD?"
date: 2014-08-19
forum: Hardware
---

### Post by ubuntom on 2014-08-19
My NAS from western digital crashed. The HDD is still in order, I think, so I opened the case of the NAS and I tried to mount it directly onto system. It was impossible to mount with the following message:


Error mounting /dev/sdb4 at /media/tom/e3c8a62d-db1d-4235-b36f-4a9c06316a85: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb4" "/media/tom/e3c8a62d-db1d-4235-b36f-4a9c06316a85"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb4, 
       missing codepage or helper program, or other error 
       In some cases useful info is found in syslog - try 
       dmesg | tail  or so 

so I tried to figur out some things :

tom@Compaq-dx2300-Microtower:~$ sudo parted -l 
Model: ATA WDC WD20EURS-63S (scsi) 
Schijf /dev/sdb: 2000GB 
Sectorgrootte (logisch/fysiek): 512B/4096B 
Partitietabel: gpt 

Nummer  Begin   Einde   Grootte  Bestandssysteem  Naam     Vlaggen 
 3      15,7MB  528MB   513MB                     primary  msftdata 
 1      528MB   2576MB  2048MB   ext3             primary  raid 
 2      2576MB  4624MB  2048MB   ext3             primary  raid 
 4      4624MB  2000GB  1996GB   ext4             primary  msftdata 

on sdb4 are the important data
sdb3 is giving the problem:

tom@Compaq dx2300 Micro Tower: ~ $ sudo fsck.ext4 -v / dev / sdb4 e2fsck 1.42.9 (4-Feb-2014) / dev / sdb4: clean, 39308/30355200 files, 17996119/30453104 blocks 
tom@Compaq dx2300 Micro Tower: ~ $ fsck -v / dev / sdb3 fsck from util-linux 2.20.1 e2fsck 1.42.9 (4-Feb-2014) fsck.ext2: Access denied while trying to open / dev / sdb3 You must have r / w access to the filesystem or being root. 
tom@Compaq dx2300 Micro Tower: ~ $ sudo fsck -v / dev / sdb3 fsck from util-linux 2.20.1 e2fsck 1.42.9 (4-Feb-2014) ext2fs_open2 (): Invalid magic number in superblock fsck.ext2: Superblock invalid - backup blocks are viewed ... fsck.ext2: Invalid magic number in super-block while trying to open / dev / sdb3 The <error> could not be read or does not describe a valid ext2 / ext3 / ext4 <error>. If the <error> is valid and it really contains an ext2 / ext3 / ext4 <error> (and not swap or ufs or something else), then the <error> is corrupt, and you might try running e2fsck with an alternate <error>: **** e2fsck-b 8193 << error >> * or **** e2fsck-b 32768 << error >>B

So, what can I do to save the data from sdb4?

---

