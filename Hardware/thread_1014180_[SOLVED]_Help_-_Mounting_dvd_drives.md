---
title: "[SOLVED] Help - Mounting dvd drives?"
date: 2008-12-17
forum: Hardware
---

### Post by Ant68 on 2008-12-17
Hi,
After a fresh install of Intrepid, I have two DVD drives that are not mounted (weirdly they read content but I cannot access them).

I believe I need to mount them before I can start to use them


**mypc@mmypc-desktop:~$ sudo lshw -short**
[sudo] password for mona: 
H/W path          Device       Class          Description
=========================================================
                               system         PROD00000000
/0                             bus            MS-6719
/0/0                           memory         128KiB BIOS
/0/4                           processor      Intel(R) Pentium(R) 4 CPU 2.80GHz
/0/4/8                         memory         8KiB L1 cache
/0/4/9                         memory         512KiB L2 cache
/0/18                          memory         512MiB System Memory
/0/18/0                        memory         256MiB DIMM SDRAM Synchronous
/0/18/1                        memory         256MiB DIMM SDRAM Synchronous
/0/100                         bridge         651 Host
/0/100/1                       bridge         Virtual PCI-to-PCI bridge (AGP)
/0/100/1/0                     display        GeForce 7300 GT
/0/100/2                       bridge         SiS962 [MuTIOL Media IO]
/0/100/2.1                     bus            SiS961/2 SMBus Controller
/0/100/2.3                     bus            FireWire Controller
/0/100/2.5        scsi0        storage        5513 [IDE]
/0/100/2.5/0      /dev/sda     disk           60GB ST360012A
/0/100/2.5/0/1    /dev/sda1    volume         54GiB EXT3 volume
/0/100/2.5/0/2    /dev/sda2    volume         1466MiB Extended partition
/0/100/2.5/0/2/5  /dev/sda5    volume         1466MiB Linux swap / Solaris partition
/0/100/2.5/0.1.0  /dev/cdrom   disk           DVD reader
/0/100/2.5/1      /dev/cdrom1  disk           CD/DVDW TS-H552B
/0/100/2.7                     multimedia     AC'97 Sound Controller
/0/100/3                       bus            USB 1.1 Controller
/0/100/3.1                     bus            USB 1.1 Controller
/0/100/3.2                     bus            USB 1.1 Controller
/0/100/3.3                     bus            USB 2.0 Controller
/0/100/4          eth0         network        SiS900 PCI Fast Ethernet
/0/100/6          wlan0        network        RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
/0/100/7          eth1         network        DP83815 (MacPhyter) Ethernet Controller
/0/100/8                       communication  536EP Data Fax Modem
/0/1              scsi2        storage        
/0/1/0.0.0        /dev/sdb     disk           750GB OneTouch
/0/1/0.0.0/1      /dev/sdb1    volume         698GiB Windows NTFS volume
/1                pan0         network        Ethernet interface

[B]
etc/mtab:[/B]
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-9-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/hemona/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=hemona 0 0
/dev/sdb1 /media/OneTouch4 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb1 /media/cdrom0 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0


**etc/fstab:**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1948d24d-a767-490d-9d69-e513ef76c0ad /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d19b101d-8f99-4e9f-b78a-07fab9bdd5c1 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


[COLOR="Red"]
Could you please help me to mount my drives? What do I need to do?[/COLOR]

---

### Post by sisco311 on 2008-12-17
post:
```
sudo lshw -C disk
```

---

### Post by taurus on 2008-12-17
> 
etc/mtab:
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-9-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/hemona/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=hemona 0 0
/dev/sdb1 /media/OneTouch4 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
**[COLOR="Blue"]/dev/sdb1 /media/cdrom0 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0[/COLOR]**

How come your /dev/sdb1 is using /media/cdrom0 as a mount point?

What are the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```

---

### Post by Ant68 on 2008-12-17
**addressing sisco311:** - taurus is below.

 sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: ST360012A
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.30
       serial: 3KC0AKE6
       size: 55GiB (60GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=b9e8b9e8
  *-cdrom:0
       description: DVD reader
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/Disk1
       capabilities: audio dvd
       configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted status=ready
  *-cdrom:1
       description: DVD writer
       product: CD/DVDW TS-H552B
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: TS04
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       product: OneTouch
       vendor: Maxtor
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 0125
       serial: 2HA19PVV
       size: 698GiB (750GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=e9865289


**_Addressing Taurus:_**
**sudo fdisk -l**

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9e8b9e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7110    57111043+  83  Linux
/dev/sda2            7111        7297     1502077+   5  Extended
/dev/sda5            7111        7297     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe9865289

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572001    7  HPFS/NTFS

**df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              54G   12G   39G  24% /
tmpfs                 252M     0  252M   0% /lib/init/rw
varrun                252M  208K  251M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M  2.8M  249M   2% /dev
tmpfs                 252M  320K  251M   1% /dev/shm
lrm                   252M  2.0M  250M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1             699G   84G  615G  12% /media/OneTouch4
/dev/sdb1             699G   84G  615G  12% /media/cdrom0

---

### Post by taurus on 2008-12-17
Try

```
sudo umount /media/cdrom0
df -h
```
Now, pop a DVD into the drive and see if it's automounted.

---

### Post by Ant68 on 2008-12-17
I am getting:

> sudo umount /media/cdrom0
Cannot create link /etc/mtab~
Perhaps there is a stale lock file?

---

### Post by sisco311 on 2008-12-17
also add a new fstab entry for the second dvd driver.
```
gksu gedit /etc/fstab
```
and add this line:
> /dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
and create the mount point:
```
sudo mkdir /media/cdrom1
```

---

### Post by taurus on 2008-12-17
Is there a program accessing /dev/sdb1 right now?

---

### Post by Ant68 on 2008-12-17
@taurus:
I have removed a CD in one of the DVD drives. I have two dvd drives (one RW the other R only).

I have now rerun the command:
sudo umount /media/cdrom0

and got:
> hemona@hemona-desktop:~$ sudo umount /media/cdrom0
umount: /media/cdrom0: not mounted


@sisco311
I added /dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0  to the fstab file.

> sudo mkdir /media/cdrom1
mkdir: cannot create directory `/media/cdrom1': File exists

---

### Post by Ant68 on 2008-12-17
adding to the diagnosis:
When I introduce a new CD disk in the CD-RW/DVD±RW Drive (RW), the drive pick up the disk.
When I introduce a new DVD disk (4.7GB) in the CD-RW/DVD±RW Drive (RW), the drive does not pick up the disk.


the problem is that I would like to burn a dvd (.iso) file.

It looks like if the drives are wrongly set up...

---

### Post by Ant68 on 2008-12-19
fixed the issue changing driver hardware...

---

