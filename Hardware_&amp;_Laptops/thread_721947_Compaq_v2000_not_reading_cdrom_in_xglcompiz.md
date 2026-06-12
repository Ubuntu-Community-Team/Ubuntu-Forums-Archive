---
title: "Compaq v2000 not reading cdrom in xgl/compiz"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by HeresJohnny on 2008-03-11
Hi everyone.  I've noticed a touchy little problem with my Compaq V2000 laptop and I was wondering if someone had any advice.  When I run XGL/Compiz, my CDROM won't mount.  I'll put in a dvd (like 'Goodfellas') so I can watch it, and nothing happens.  I later find out that the drive hasn't mounted.  I don't experience the problem if I switch to a regular gnome session.  Any insights?  I'll post some Level 3 diagnostics below:

```
heresjohnny@heresjohnny-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=723d0ca8-9f01-492c-838f-b3de0157bbcc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=8250b67d-0aff-4775-b4bc-96b59adb7df5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
 sudo lshw -C disk
[sudo] password for heresjohnny:
  *-disk                  
       description: ATA Disk
       product: IC25N060ATMR04-0
       vendor: Hitachi
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: MO3OAD5A
       serial: MRG31YKKJ1YENH
       size: 55GB
       capacity: 55GB
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma5 smart=on
  *-disk
       description: SCSI Disk
       product: USB DISK
       vendor: SMI
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 1100
       serial: (&#65533;&#65533;&#65533;&#65533; 1100&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                                       @m
       size: 105MB
       capabilities: removable
     *-disc
          physical id: 0
          logical name: /dev/sda
          size: 105MB
          capabilities: partitioned partitioned:dos

```

Anyway, it's not a huge deal, but I was wondering if anyone else was having the same problem.

---

