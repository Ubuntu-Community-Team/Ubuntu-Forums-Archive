---
title: "DVD drive doesn't read DVDs"
date: 2010-04-13
forum: Hardware
---

### Post by Don Gatto on 2010-04-13
Hi,

A friend of mine has a strange problem with his disk drive.
Reading or writing CDs: yes.
Noticing and writing blank DVDs: yes.
Reading any kind of DVD: no.

He had 8.04 before where he started experiencing the problem after an update. Now he has a fresh install of 9.04.
The problem doesn't exist on his fresh Windows XP.

I've spent a half day searching the web and trying to apply tips, but didn't succeed.

The drive is an NEC ND-4550A. I updated its firmware from 1.06 to 1.09.

Here are the most important commands I've tried and their outputs:
```

uname -a
Linux beregszaszi-desktop 2.6.28-18-generic #60-Ubuntu SMP Fri Mar 12 04:40:52 UTC 2010 i686 GNU/Linux
```

```
$ sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD_RW ND-4550A
       vendor: _NEC
       physical id: 0.1.0
       bus info: scsi@2:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.09
       serial: [_NEC    DVD_RW ND-4550A 1.0906092800
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
```

```
sudo sg_scan -i
/dev/sg0: scsi0 channel=0 id=0 lun=0 [em]
    ATA       Hitachi HDT72503  V54O [rmb=0 cmdq=0 pqual=0 pdev=0x0] 
/dev/sg1: scsi2 channel=0 id=1 lun=0 [em]
    _NEC      DVD_RW ND-4550A   1.09 [rmb=1 cmdq=0 pqual=0 pdev=0x5]
```

There isn't any other drive in this computer.

```
wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : '_NEC' 'DVD_RW ND-4550A'
-------------------------------------------------------------------------
```

```
wodim -scanbus
scsibus2:
	2,0,0	200) *
	2,1,0	201) '_NEC    ' 'DVD_RW ND-4550A ' '1.09' Removable CD-ROM
	2,2,0	202) *
	2,3,0	203) *
	2,4,0	204) *
	2,5,0	205) *
	2,6,0	206) *
	2,7,0	207) *

```

Manually added to /etc/fstab:
```
/dev/sr0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Tried with alternate file system order, alternate devices etc. It didn't make a change.

```
ls -l /dev/sr0 /dev/scd0
lrwxrwxrwx  1 root root      3 2010-03-25 16:04 /dev/scd0 -> sr0
brw-rw----+ 1 root cdrom 11, 0 2010-03-25 16:04 /dev/sr0
```

The command eject /dev/sr0 works.


After inserting a DVD:
```
sudo mount /dev/sr0
sudo mount /dev/scd0
sudo mount -t iso9660 /dev/disk/by-path/pci-0000\:00\:06.0-scsi-0\:0\:1\:0 /media/cdrom0
sudo mount -t udf /dev/disk/by-path/pci-0000\:00\:06.0-scsi-0\:0\:1\:0 /media/cdrom0

mount: no medium found on /dev/sr0

or

mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

```
dmesg | tail
[ 1482.254249] attempt to access beyond end of device
[ 1482.254259] sr0: rw=0, want=68, limit=4
[ 1482.261035] attempt to access beyond end of device
[ 1482.261041] sr0: rw=0, want=1028, limit=4
[ 1482.261052] attempt to access beyond end of device
[ 1482.261057] sr0: rw=0, want=2052, limit=4
[ 1482.261065] UDF-fs: No partition found (1)
[ 1482.280817] attempt to access beyond end of device
[ 1482.280827] sr0: rw=0, want=68, limit=4
[ 1482.280834] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
```

Removed /etc/udev/rules.d/70-persistent-cd.rules, didn't help.

Nautilus said little in its message box: 
Unable to mount location
Unable to mount volume.

Do you have any ideas on the source of the issue and perhaps the solution to it as well?

Thank you and all the best,
Marci

---

### Post by Kevbert on 2010-04-13
Do you have the library libdvdread4 installed ? It's in the Universe Repo.
It can be installed via terminal with
```
sudo apt-get install libdvdread4
```

---

### Post by khelben1979 on 2010-04-13
[libdvdcss]("http://en.wikipedia.org/wiki/Libdvdcss") is also good to have for reading DVDs.

[libdvdcss download]("http://download.videolan.org/pub/libdvdcss/") from the videolan homepage.

---

### Post by bart.vanaudenhove on 2010-05-01
I had a similar problem on my HP Laptop: any data cd or DVD would read and write fine, but audio cds and movie dvds would not be recognized.

For me the solution was to physically slip the optical drive out of the computer (unscrew a vise in the back and push the drive a bit out) = unplugged and power off off course =, plug it back in, and at next startup everything was fine. (I found it in another post somewhere)

From time to time the same problem reappears and the same solutions works for a while...

This is in Ubuntu 9.10.

---

