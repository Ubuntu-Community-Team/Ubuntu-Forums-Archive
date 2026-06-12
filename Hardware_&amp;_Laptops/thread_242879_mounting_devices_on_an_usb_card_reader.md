---
title: "mounting devices on an usb card reader"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by nedkelly on 2006-08-24
Hi I have got a new card reader

The problem is that usb keys and other cards are not mounted automatically and when I mount them manually I can not write to them!!

I have search the forum but not found a solution

so can somebody please help

the dmesg when I plugin the card reader


```
 USB Mass Storage support registered.
[17193203.308000]   Vendor: OTi       Model: CF CARD Reader    Rev: 2.00
[17193203.308000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17193203.368000] Driver 'sd' needs updating - please use bus_type methods
[17193203.484000]   Vendor: OTi       Model: SM CARD Reader    Rev: 2.00
[17193203.484000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17193203.920000]   Vendor: OTi       Model: SD CARD Reader    Rev: 2.00
[17193203.920000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17193204.356000]   Vendor: OTi       Model: MS CARD Reader    Rev: 2.00
[17193204.356000]   Type:   Direct-Access                      ANSI SCSI revision: 00

```

the dmesg when I insert a card

```
[17196922.836000] SCSI device sdd: 960512 512-byte hdwr sectors (492 MB)
[17196922.836000] sdd: Write Protect is off
[17196922.836000] sdd: Mode Sense: 03 00 00 00
[17196922.836000] sdd: assuming drive cache: write through
[17196922.836000]  sdd: sdd1

```


if I would like to mount the device sdd1 I use the following command

```
sudo mount /dev/sdd1 /media/usbdrive
```

and finally my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>   <options>	       			<dump>  <pass>
proc            /proc           proc     defaults 	     			  0       0
/dev/hda2       /               reiserfs notail		         		  0       1
/dev/hda1       /media/hda1     ntfs     defaults,nls=utf8,umask=007,gid=46	  0       1
/dev/hda4       /media/hda4     vfat     defaults,utf8,umask=000		  0       0
/dev/hda3       none            swap     sw              			  0       0
/dev/hdb1	/media/e-drev	vfat	 defaults,utf8,umask=000		  0	  0
/dev/hdb2	/media/hdb2	reiserfs defaults
/dev/hdb3	/media/f-drev	ext2	 defaults				  0       0 
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto    			  0       0
```

---

