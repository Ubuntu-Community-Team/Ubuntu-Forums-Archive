---
title: "Mount: hde/hdf/hdg/hdh does not exist?"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by Marinmo on 2005-06-07
Hi there

I installed from Install CD earlier today. I have 6 harddrives attatched; sda, sdb, hde, hdf, hdg and hdh. sda + sdb is attatched to the motherboard's SATA controller, while hde - h is connected through a FastTrack TX2000. My DVD-drives (2) is hda and hdb, attatched to the motherboard aswell.

I installed Ubuntu to sda (in order to be able to boot. long story.), having /boot, swap and / on sda and /home on sdb. hde - h was not RAIDed and sat at separate mountpoints (/doc, /share etc). All was nice and dandy until I finished my install and booted up my newly acquired ubuntu-install. On mounting (during startup) hde - h the following error ocurred (I can't cite exactly since it's quite a lot of text, but you'll probably get the idea ...);
```
Failed to open the device '/dev/hde': No such file or foler
 
[...] (same for all 4 HDDs)

fsck. failed
```
My system still allows me to boot up pressing Ctrl+D, but my discs remain unmounted. It does not matter which FS I use on them; atm I use RFS but that's more or less only because I have been trying around with different FS:es to check if that was the problem.

I read some threads about similar (but not the same in essence) problems; and I thought this info might come in handy:
```
root@greenmoore:/home/marinmo # cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/hdh1       /doc            reiserfs defaults        0       2
/dev/hde1       /download       reiserfs defaults        0       2
/dev/sdb1       /home           ext3    defaults        0       2
/dev/hdg1       /share          reiserfs defaults        0       2
/dev/hdf1       /stuff          reiserfs defaults        0       2
/dev/sda2       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```
```
root@greenmoore:/home/marinmo # dmesg | grep hd
SCSI device sda: 72303840 512-byte hdwr sectors (37020 MB)
SCSI device sda: 72303840 512-byte hdwr sectors (37020 MB)
SCSI device sdb: 72303840 512-byte hdwr sectors (37020 MB)
SCSI device sdb: 72303840 512-byte hdwr sectors (37020 MB)
hda: _NEC DVD_RW ND-1300A, ATAPI CD/DVD-ROM drive
hdb: DVD-ROM DDU1621, ATAPI CD/DVD-ROM drive
hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
hdb: ATAPI 40X DVD-ROM drive, 512kB Cache
    ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
    ide2: BM-DMA at 0xdf80-0xdf87, BIOS settings: hde:pio, hdf:pio
    ide3: BM-DMA at 0xdf88-0xdf8f, BIOS settings: hdg:pio, hdh:pio
hde: WDC WD800JB-00CRA1, ATA DISK drive
hdf: WDC WD800JB-00CRA1, ATA DISK drive
hde: max request size: 128KiB
hde: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
hde: cache flushes not supported
hdf: max request size: 128KiB
hdf: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
hdf: cache flushes not supported
e1000: eth0: e1000_watchdog: NIC Link is Up 10 Mbps Full Duplex
hdg: WDC WD800JB-00CRA1, ATA DISK drive
hdh: WDC WD800JB-00CRA1, ATA DISK drive
hdg: max request size: 128KiB
hdg: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
hdg: cache flushes not supported
hdh: max request size: 128KiB
hdh: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
hdh: cache flushes not supported
SCSI device sdc: 7999488 512-byte hdwr sectors (4096 MB)
SCSI device sdc: 7999488 512-byte hdwr sectors (4096 MB)
```
```
root@greenmoore:/home/marinmo # cat /etc/modules
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

Any help on this would be beyond appreciated. I'm baffled; FC4 managed to mount it all just fine, and I have no idea what I've done different here. Thank you for your time.

---

### Post by lawngn0mex on 2005-06-07
That's strange. I haven't used a PCI IDE controller with Ubuntu, but in the past (other distros) I've seen the drives connected to the PCI IDE controller treated as SCSI, SDA SDB ect....

you try just making a directory and mounding HDE1 to something like /media/electricboogaloo/ forgoinf the FSTAB and all of that jazz?

---

### Post by Marinmo on 2005-06-07
[QUOTE=lawngn0mex]That's strange. I haven't used a PCI IDE controller with Ubuntu, but in the past (other distros) I've seen the drives connected to the PCI IDE controller treated as SCSI, SDA SDB ect....

you try just making a directory and mounding HDE1 to something like /media/electricboogaloo/ forgoinf the FSTAB and all of that jazz?[/QUOTE]
Now this is odd .... Mounting it like you said (mount /dev/hde1 /media/blah) worked (I haven't tried rebooting yet though, I just did it through a normal terminal). I'll reboot asap and edit this post with the results of it. Thank you.

EDIT:
It did not work. I am completely clueless;
"mount: special device /dev/hde1 could not be mounted"

Anyone? Note; I can still mount it now, when I'm actually *in* the OS - it's just the startup that's not working ... At all.

---

