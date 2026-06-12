---
title: "DVD Drive Stuck at Spinning Up"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by HoberShort on 2007-12-26
On this Gateway MX6421 laptop I'm using, it has a combo DVD/CD drive with a few flavors of plus and minus "R"s. 

At any rate, when I first got it home, the first thing I did was watch a DVD movie on it (The Matrix). This was on Windows. 

Some time later, when this laptop was running both Kubuntu and Windows, I tried to watch a DVD and found that inserting a DVD causes the drive to spin up and whir for a moment, and then spin down. This repeats a half dozen times until the drive rests. This happens in both operating systems.

Also, when the BIOS is booting, if there is a DVD in the drive, it will attempt to boot from, or at least read, the DVD, with the same up-and-down effect. 

I had consigned myself to this being a faulty drive, or at least some problem that was operating system independent (identical symptoms in each of two operating systems, as well as in neither of them). That was, until today. I decided to try and give it one more shot.

And for a short, glorious time, I was able to make it work. When I inserted a disc, the spinning would begin, but the issuing of a "hdparm /dev/hdc" (hdc being my CD/DVD drive) would cause the spinning to end and an icon to appear on the desktop and in /media. Exploring this showed me wonderful vistas, rich with VOBs and BUPs. 

But alas, this time has passed. With no change I can recollect, the system has returned to its old ways, of interminable spinning. 

At the beginning of the short period of functionality, I had just installed dvd::rip and libdvdcss2, for self-evident purposes. I am unsure if this ushered in the period of bliss, or was merely correlated with it.

So was my original assumption that the hardware is faulty correct? Or is there some way, through the arcane manipulation of bits, to bring about a second epoch of DVD function?

What follows are what seem to be the standard troubleshooting commands for a similar problem:
```
$ sudo lshw -C disk
  *-disk
       description: ATA Disk
       product: HTS421280H9AT00
       vendor: Hitachi
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: HA3OA70G
       serial: HKA310AKGJJ04B
       size: 74GB
       capacity: 74GB
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma5 smart=on
  *-cdrom
       description: DVD writer
       product: PHILIPS DVD+/-RW SDVD8441
       vendor: Philips
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: PA49
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma2 status=nodisc
```

(The "status = nodisc" here is of particular interest to me.)

```
$ hdparm /dev/hdc

/dev/hdc:
 IO_support    =  0 (default 16-bit)
 unmaskirq     =  0 (off)
 using_dma     =  1 (on)
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=ab9686a9-6d0c-448c-a9be-abc6767edc51 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=7A305EEA305EAD3F /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda2
UUID=6A5F-1690  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=d0cc32ba-aac0-4f8a-b13e-4fa7e7a94f6d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

