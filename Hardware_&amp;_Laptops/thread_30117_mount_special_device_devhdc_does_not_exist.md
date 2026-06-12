---
title: "mount: special device /dev/hdc does not exist"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by robza on 2005-04-27
Hi everyone

I installed hoary 10 minutes ago from dvd, in the dvd drive attached to what should be /dev/hdc. Now, I'm getting this error message whenever I try to use the drive. What's wrong? I've seen lots of other people post this problem, and have never seen a working fix for it...

My setup: 
- Two hard disks on the primary ide channel (a seagate and a maxtor). Both work great. 
- An LG GSA4082B DVD-RAM drive as the master on the secondary channel (not working)
- An AOPEN CRW5232 CD rewriter as slave on the secondary channel (works great)

Here's some stuff that might be useful:

```
root@apodyopsis:/home/rstark # cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /monolith       vfat    defaults        0       0
/dev/hdb1       /slab           vfat    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
```

```
root@apodyopsis:/home/rstark # dmesg |grep hd
Kernel command line: root=/dev/hda6 ro quiet splash
    ide0: BM-DMA at 0xc800-0xc807, BIOS settings: hda:pio, hdb:pio
    ide1: BM-DMA at 0xc808-0xc80f, BIOS settings: hdc:pio, hdd:pio
hda: Maxtor 6Y160P0, ATA DISK drive
hdb: ST3120026A, ATA DISK drive
hda: max request size: 1024KiB
hda: 320173056 sectors (163928 MB) w/7936KiB Cache, CHS=19929/255/63, UDMA(133)
hda: cache flushes supported
hdb: max request size: 1024KiB
hdb: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
hdb: cache flushes supported
hdd: AOPEN CD-RW CRW5232 1.05 20040324, ATAPI CD/DVD-ROM drive
Adding 971892k swap on /dev/hda7.  Priority:-1 extents:1
EXT3 FS on hda6, internal journal
hdd: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache

```

Note the lack of any DVD drive, or hdc, there...

```
root@apodyopsis:/home/rstark # cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod
```


Please help, I think that ubuntu is great but I'll have to go back to slackware if I can't get my dvd drive working :( everything works fine under windows xp, knoppix 3.8, and the warty livecd...

Thank you
rob

---

### Post by ssam on 2005-04-27
i might be wrong but it could be a problem with hotplug not creating the /dev/ files.
try
```
ls /dev/ | grep hd
```
and see if hdc is created.

if not then the solution is
```
cd /etc/udev/rules.d
sudo ln -s ../cd-aliases.rules
```

(see [Hoary Upgrade Notes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)  and [bug 7789](https://bugzilla.ubuntu.com/show_bug.cgi?id=7789#c3))

---

### Post by robza on 2005-04-27
Hi, thanks for the quick reply :)

Unfortunately, it didn't work :( 
hdc didn't exist in /dev/, but cd-aliases.rules already existed in /etc/udev/rules.d.

the contents of that file is:

```
root@apodyopsis:/etc/udev/rules.d # cat cd-aliases.rules
# These rules create the /dev/{cdrom,dvd,...} symlinks. Also see the
# /etc/udev/cdsymlinks.conf config file.
#
# If you would like to statically configure the aliases instead, you can
# use rules like:
# BUS="ide", ID="1.0", SYMLINK="cdrom"

BUS="scsi", KERNEL="sr[0-9]*",                        PROGRAM="/etc/udev/scripts/cdsymlinks.sh %k", SYMLINK="%c{1} %c{2} %c{3} %c{4} %c{5} %c{6}"
BUS="ide",  KERNEL="hd[a-z]",   SYSFS{removable}="1", PROGRAM="/etc/udev/scripts/cdsymlinks.sh %k", SYMLINK="%c{1} %c{2} %c{3} %c{4} %c{5} %c{6}"
BUS="ide",  KERNEL="pcd[0-9]*", SYSFS{removable}="1", PROGRAM="/etc/udev/scripts/cdsymlinks.sh %k", SYMLINK="%c{1} %c{2} %c{3} %c{4} %c{5} %c{6}"
```

btw, this isn't an upgrade; i did a totally clean install.

any more ideas?

thanks
rob

---

### Post by recek on 2005-11-17
the same for me
but i resolved it!
my matsushita DVDR must be settet as Secondary Slave,
so it WORKS!
:D :KS

---

