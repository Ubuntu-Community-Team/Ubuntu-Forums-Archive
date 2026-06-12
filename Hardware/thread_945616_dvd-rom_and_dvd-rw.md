---
title: "dvd-rom and dvd-rw"
date: 2008-10-12
forum: Hardware
---

### Post by efeurich on 2008-10-12
Hi,

My system has two dvd drive 1= dvd-ROM and the other is dvd-RW.
The dvdrom works fine and is automatically gets detected when i insert a cd/dvd.
The dvd-rw doesn't get recognized.In my fstab i see two cdrom entries:
UUID=050e0b55-12ab-47d5-bfa8-c0a267477f2a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

Is this correct. Should this be cdrom entries or should this be DVDRW entries?

When i try to get the uuid from the scd0 the output is:

ID_FS_USAGE=filesystem
ID_FS_TYPE=udf
ID_FS_VERSION=
ID_FS_UUID=
ID_FS_UUID_ENC=
ID_FS_LABEL=JOSH_GROBAN_AWAKE
ID_FS_LABEL_ENC=JOSH_GROBAN_AWAKE
ID_FS_LABEL_SAFE=JOSH_GROBAN_AWAKE

when i try to get the UUID from scd1 i get:
/dev/scd1: error opening volume

Can anyone give me some pointers?

Thanks in advanced

EIF

---

### Post by sisco311 on 2008-10-12
post:
```
sudo lshw -C disk
```

---

### Post by efeurich on 2008-10-12
When i run this command I only see 1 dvd-rom ) the one thta is working) and an other cd-rom. But the drive that is connected is a DVD-RW.

Does this means that there is a hardware problem with the dvd-rw drive?

EIF

---

### Post by sisco311 on 2008-10-12
Please post the output of the command.

---

### Post by efeurich on 2008-10-12
Here it is.....
Both dvd drives are connected to one IDE interface as master and slave.

 *-cdrom:0               
       description: DVD reader
       product: DVD-ROM GDR8164B
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 0L06
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: SCSI CD-ROM
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/scd1
       logical name: /dev/sr1
       capabilities: audio
       configuration: status=open
  *-disk
       description: ATA Disk
       product: ST3160215AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 6RA1XZBH
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0778dc8a
  *-disk
       description: SCSI Disk
       product: SP1604N
       vendor: SAMSUNG
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
       version: 0000
       serial: 0S311JA0
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=2d87cdb5

---

### Post by sisco311 on 2008-10-12
Insert a cd/dvd in the drive and try to mount it from a terminal:
```
sudo mount -t udf,iso9660 -o loop /dev/scd1 /media/cdrom1
```

Post the error message if any.

---

### Post by efeurich on 2008-10-12
Hi,

It seems to work. It mounted under the name cdrom1.
I know that i can make this automatic by applying this ti the fstab file.
But for this i need to have the uuid of the drive...i think.

So how can i get the uuid of the dvd-rw drive?

---

### Post by sisco311 on 2008-10-12
while the cd/dvd is mounted post the output of:
```
mount
```and
```
sudo lshw -C disk
```

---

### Post by efeurich on 2008-10-12
Mount output:
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-rt/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sda1 on /media/SWEEX type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=eric)
/dev/scd1 on /media/cdrom1 type udf (ro,loop=/dev/loop0)

output of lshw -C disk

 *-cdrom:0               
       description: DVD reader
       product: DVD-ROM GDR8164B
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 0L06
       capabilities: removable audio dvd
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
  *-cdrom:1
       description: SCSI CD-ROM
       product: DVDR   PX-716A
       vendor: PLEXTOR
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.11
       capabilities: removable audio
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: ATA Disk
       product: ST3160215AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 3.AA
       serial: 6RA1XZBH
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0778dc8a
  *-disk
       description: SCSI Disk
       product: SP1604N
       vendor: SAMSUNG
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 0000
       serial: 0S311JA0
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=2d87cdb5

---

### Post by sisco311 on 2008-10-12
in fstab try to change:
> /dev/**scd1** /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0to
> /dev/**cdrom** /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

edit the file as root:
```
gksu gedit /etc/fstab
```
save the file and reboot.

---

### Post by efeurich on 2008-10-12
Hi, 

Nothing mounted automatically on start up.
Should it have?
fstab file content:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9e285416-0b91-47ff-b8e7-7ee23204ffdd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=050e0b55-12ab-47d5-bfa8-c0a267477f2a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/cdrom       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

---

