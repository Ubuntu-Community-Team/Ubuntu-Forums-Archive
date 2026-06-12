---
title: "Error when mounting local HDD: wrong fs type, bad option, bad superblock on /dev/sdb1"
date: 2014-04-16
forum: Hardware
---

### Post by Jorge_Molero on 2014-04-16
Suddenly, when trying to access one of my local HDD, I get this error:
Error mounting /dev/sdb1 at /media/j/STORAGE2: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/j/STORAGE2"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When doing dmesg | tail and sudo parted -l i get this
j@j-RC415T-M2:~$ dmesg | tail
[ 1072.289605] blk_update_request: 47 callbacks suppressed
[ 1072.289608] end_request: I/O error, dev sdb, sector 65
[ 1072.289625] EXT4-fs (sdb1): unable to read superblock
[ 1344.768110] sd 3:0:0:0: [sdb] Unhandled error code
[ 1344.768117] sd 3:0:0:0: [sdb]  
[ 1344.768121] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[ 1344.768124] sd 3:0:0:0: [sdb] CDB: 
[ 1344.768127] Read(10): 28 00 00 00 00 41 00 00 02 00
[ 1344.768140] end_request: I/O error, dev sdb, sector 65
[ 1344.768157] EXT4-fs (sdb1): unable to read superblock
j@j-RC415T-M2:~$ ^C
j@j-RC415T-M2:~$ sudo parted -l
[sudo] password for j: 
Modelo: ATA WDC WD1600BEVS-6 (scsi)
Disco /dev/sda: 160GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin    Tamaño  Tipo      Sistema de archivos  Banderas
 1      1049kB  100GB  100GB   primary   ext4                 arranque
 2      100GB   158GB  58,0GB  primary   fat32
 3      158GB   160GB  2041MB  extended
 5      158GB   160GB  2041MB  logical   linux-swap(v1)


Error: /dev/sdb: etiqueta de disco no reconocida                          

Modelo: ATA ST380011A (scsi)
Disco /dev/sdc: 80,0GB
Tamaño de sector (lógico/físico): 512B/512B
Tabla de particiones. msdos

Numero  Inicio  Fin     Tamaño  Tipo     Sistema de archivos  Banderas
 1      1049kB  80,0GB  80,0GB  primary  fat32                arranque

---

### Post by bazsound on 2014-04-16
thats not good.
Id run some diagnostics on the drive. its possible it has failed or has started to fail and there is corruption.

Open up gparted and see if it can atleast see the drive to check what its reporting is on it.

---

