---
title: "No UDF DVD support?? fstabs udftools rlly?? UBUNTU Cant Mount UDF"
date: 2007-11-18
forum: Hardware &amp; Laptops
---

### Post by nae5 on 2007-11-18
Does Ubuntu really not have support for reading UDF DVD-R discs?  Or is it my particular hardware?  Or lack of package or ??

     I have an old music collection that i have never been able to use with ubuntu.  man.. these are cds from middle school and stuff ) 

     These discs were burned under windows xp home by drag and drop (probably using the roxio software that came with it ) .  The dvd s are read fine on a windows xp computer and the files all work fine.

The manual attempt:

```
naes@naestwo:~$ sudo mount -t udf /dev/scd0 /media/cdrom0
[sudo] password for naes:
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

naes@naestwo:~$ 
```

the dmesg | tail   

```
naes@naestwo:~$ dmesg | tail
[ 9389.487436] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[ 9406.471785] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[ 9698.246415] grow_buffers: requested out-of-range block 18446744073709186160 for device sr0
[ 9701.912837] attempt to access beyond end of device
[ 9701.912851] sr0: rw=0, want=23705188, limit=8260992
[ 9701.912862] attempt to access beyond end of device
[ 9701.912868] sr0: rw=0, want=23704964, limit=8260992
[ 9701.912873] UDF-fs: No partition found (1)
[ 9756.149310] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
[ 9762.143730] wifi0: invalid skb->cb magic (0x00000000, expected 0xf08a36a2)
naes@naestwo:~$ 
```


These are the drives on my ubuntu pc
lshw
```
*-cdrom:0
                description: DVD reader
                product: DVD-ROM DVD-115
                vendor: PIONEER
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.22
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=ready
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: CD-RW CED-8120B
                vendor: LG
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.03
                serial: LG      CD-RW CED-8120B 1.03
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=open
        *-usb:0
```

fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=80e6490c-dfcd-4af3-b034-4b904a061b7d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8ef01675-a70c-44a3-939f-e4d45479dec6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto rw,user,noauto.exec 0       0
/dev/scd1       /media/cdrom1   auto rw,user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto rw,user,noauto,exec 0       0

```
note fstab originally had 

udf,iso9660 user,noauto,exec 0     0
udf,iso9660 user,noauto,exec 0     0
auto rw,user,noauto,exec 0     0

im pretty positive i didn't miss any there but it shouldn't matter since it wasn't working anyways no?



also while reading other troubleshoots on this and installing udftools i came across mention of this file /etc/default/udftools and don't know if the fact that it says "NAMES" all over and doesn't name either my cddvdrom or cdrw drives right

```
# Drives to register for packet writing:
#DEVICES="/dev/hdd /dev/sr0"

# Pktcdvd patches for kernels 2.6.8 and later use a new interface for
# talking to the kernel, as well as a new set of device nodes. In case
# detection of the proper interface on your system fails, override
# it here. Possible values are "true" or "false".
#NEWINT=true

# Only when using the new interface do you have the option to choose the
# names for the packet writing devices. This is ignored otherwise.
# For example, if DEVICES="/dev/hdd /dev/sr0" and
# NEWINTNAMES="cdwriter dvdwriter", then /dev/hdd will correspond to
# /dev/pktcdvd/cdwriter, and /dev/sr0 will correspond to
# /dev/pktcdvd/dvdwriter. The default setting is NEWINTNAMES="0 1 2 3".
#NEWINTNAMES="0 1 2 3"
```

I tried changing "#DEVICES="/dev/hdd /dev/sr0""  to /dev/scd0 /media/cdrom0  but it didn't work


There are numerous others with similar problems here are some of the links ive been looking at

[http://ubuntuforums.org/showthread.php?t=616674&highlight=UDF+dvd](http://ubuntuforums.org/showthread.php?t=616674&highlight=UDF+dvd)
[http://www.uluga.ubuntuforums.org/showthread.php?t=510748](http://www.uluga.ubuntuforums.org/showthread.php?t=510748)

Any help would be much appreciated i think ubuntu should be able to mount and read UDF multimedia discs they are very common

---

### Post by nae5 on 2007-11-19
guys im super serial

---

### Post by kornelix on 2007-12-05
This is no help, just some confirmation of your worst fears. I tried out the UDF file system and found the software to be too unreliable to use. I was able to write some files and read them, along with all the hangups and crashes.

I use the iso9660 file system which is serial (not packet) but at least works well.

Good luck.

---

### Post by kornelix on 2007-12-05
Note that Nero is available for Linux. Try gnomefiles.org. I have no idea how well it works, but it is quite popular.

---

### Post by thewarlock on 2007-12-08
I get this same problem with some of my DVDs.

Under 7.04 by changing the fstab I could manually mount the drives and copy the files off.

Right now, it mounts them, but you can't get the files directly. I CAN however copy the entire disk over to a .iso file and then extract the files.

... popping the dvd in and the icon shows on the desktop. Can't do anything with it except eject and copy the entire disk.

Manual mount just either does the same thing, or gives the error the OP mentioned.

(the disks themselves are fine)

This happens on several machines, some with just DVD players, others with RW drives.

---

### Post by thewarlock on 2007-12-13
try

/dev/scd0       /media/cdrom0   iso9660,udf user,noauto     0       0


that made it work for me.

Seems the problems is in the permissions. UDF honors them (even if they are insane)

(got this by searching the bug forums for udf)

---

