---
title: "HighPoint Rocket Raid 454 driver compile errors"
date: 2009-12-29
forum: Hardware
---

### Post by ethersphere on 2009-12-29
I have a raid 5 setup on my rocketraid 454 but ubuntu does not recognize it as it should; instead it displays each disk seperately.

Right now, fdisk -l shows each disk separately as the default driver does not work.

****fdisk -l RESULTS*********
Disk /dev/sda: 30.8 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f9e5f9e

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3707    29776446   8e  Linux LVM
/dev/sda2            3708        3738      249007+   5  Extended
/dev/sda5            3708        3738      248976   83  Linux

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b44a489

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       44841   360179712    7  HPFS/NTFS

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b44a489

  Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       44841   360179712    7  HPFS/NTFS
*******end results**************

I tried downloading the drivers directly from the highpoint website [http://www.highpoint-tech.com/BIOS_Driver/hpt374/Linux/hpt374-src-v2.19-080710.tgz](http://www.highpoint-tech.com/BIOS_Driver/hpt374/Linux/hpt374-src-v2.19-080710.tgz), extracting the files, and attempted to compile.  Doing so yields the following results:

*********Begin make results************

ethersphere@Raptor:~$ make KERNELDIR=/usr/src/linux-headers-2.6.31-14-generic-pae/ RR154X=0
cp -f raid.o raid.obj
make -C /usr/src/linux-headers-2.6.31-14-generic-pae/ SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic-pae'
CC [M] /home/ethersphere/hpt.o
/home/ethersphere/hpt.c: In function 'get_bdev':
/home/ethersphere/hpt.c:114: error: too many arguments to function 'blkdev_get'
/home/ethersphere/hpt.c:118: error: too few arguments to function 'blkdev_put'
/home/ethersphere/hpt.c: In function 'sd_inuse':
/home/ethersphere/hpt.c:131: error: too few arguments to function 'blkdev_put'
In file included from /home/ethersphere/hpt.c:164:
/home/ethersphere/entry.c: In function 'do_mode_sense':
/home/ethersphere/entry.c:382: error: 'SUGGEST_ABORT' undeclared (first use in this function)
/home/ethersphere/entry.c:382: error: (Each undeclared identifier is reported only once
/home/ethersphere/entry.c:382: error: for each function it appears in.)
/home/ethersphere/entry.c: In function 'OsSendCommand':
/home/ethersphere/entry.c:457: error: 'SUGGEST_ABORT' undeclared (first use in this function)
In file included from /home/ethersphere/hpt.c:164:
/home/ethersphere/entry.c: In function 'fOsCommandDone':
/home/ethersphere/entry.c:1235: error: 'SUGGEST_ABORT' undeclared (first use in this function)
In file included from /home/ethersphere/hpt.c:165:
/home/ethersphere/hptproc.c: In function 'get_sd_name':
/home/ethersphere/hptproc.c:505: error: too few arguments to function 'blkdev_put'
make[2]: *** [/home/ethersphere/hpt.o] Error 1
make[1]: *** [_module_/home/ethersphere] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic-pae'
make: *** [default] Error 2

****************END make results**************

I have read in the forums that some have gotten this to compile in versions 2.6.18, as you noticed I have 2.6.30+

Apparently, somewhere along the line between those two kernel versions an update broke the drivers.  I tried looking for documentation on those functions that are throwing the errors and make the necessary changes myself, but documentation is scarce and I have no prior experience coding for linux.

I'd appreciate any kind of help, including a walkthrough to downgrading to 2.6.18 if necesarry.  Thank you.

---

### Post by ethersphere on 2010-01-01
Reply from highpoint support:

> Hello,

Updates may be released, but a date has not been set.
We have not tested past 2.6.25.
Others have reported success with more recent versions.

Regards,

Customer Support Department

---

### Post by ethersphere on 2010-01-09
I tried installing an earlier version of ubuntu from scratch(8.X) only to receive a grub boot error that I could not remedy.

Eventually I installed FreeNAS and was able to set everything up as I wanted.  FreeNAS supports my card right out of the box and provides the file sharing for linux, mac, and windows machines as well as UPNP for PS3 XBOX Etc.

---

