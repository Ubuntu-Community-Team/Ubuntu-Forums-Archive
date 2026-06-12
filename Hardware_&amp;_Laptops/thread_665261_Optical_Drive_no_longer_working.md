---
title: "Optical Drive no longer working"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by mofmog on 2008-01-12
I am running a Dell Inspiron 1420 (not an n). Anyways, I used to run Ubuntu 7.10 with Vista. Well after I updated Vista, the Vista installation died for some reason. So I boot up to Ubuntu and start to mess around with the partition and accidentally I managed to destroy the windows install. For some reason, I couldn't boot from CD to reinstall windows so I had to boot up from a USB flash drive. I accidentally formatted the drive- so I had to basically reinstall Ubuntu from a bootable usb flash drive.

Oh well :(

So now Ubuntu is running again, ALONE. It works perfectly- wireless works, video card works, flash drive works, sound works. Except of course- the optical drive doesn't work. What's funny though is that Ubuntu recognizes that some sort of optical drive exists- it even knows what brand and what sort of optical media it can read!

I figured this was a simple error because Ubuntu probably thinks the flash drive is a cd so I messed around with /etc/fstab. No dice. This is what I have so far:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3fb24f31-271d-424e-bff5-44943110c5b8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=26a8bff1-13cf-4fef-8e64-0db87e1c71d7 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto 0       0
/dev/sdb1 /mnt/flash vfat user,noauto,umask=0 0 0

```

Here is my fdisk -l

```

Disk /dev/sdb: 1998 MB, 1998585856 bytes
255 heads, 63 sectors/track, 242 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         242     1943833+   b  W95 FAT32

```

Here is my lshw -C disk

```

  *-cdrom                 
       description: DVD writer
       product: DVD+-RW TS-L632D
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: DE04
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: Hitachi HTS72201
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: DCDO
       serial: 070626DP0D00DVG0YPDA
       size: 149GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk
       description: SCSI Disk
       product: DataTraveler 2.0
       vendor: Kingston
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: PMAP
       size: 1906MB
       capabilities: removable
     *-disc
          physical id: 0
          logical name: /dev/sdb
          size: 1906MB
          capabilities: partitioned partitioned:dos

```

---

### Post by MobiusNZ on 2008-01-12
> **mofmog said:**
> For some reason, I couldn't boot from CD to reinstall windows so I had to boot up from a USB flash drive. 

So you're telling me you can't read the cd in Windows OR Linux... sounds like grounds for a warranty return.

---

### Post by mofmog on 2008-01-12
Must be. I thought it might actually work now that I can boot into Ubuntu.

Ubuntu can detect that there is a optical drive- it can even apparently tell me the model and vendor. 

Even the BIOS detects the drive. I removed the drive, and restarted and the entry for the drive in the BIOS disappeared so I know that it's sending some sort of information outward. I guess maybe the motor is broken or something?

I dont know why it'd be working one minute and then not the next.

Luckily Dell is sending a replacement. Hope it lasts longer than this one =/

---

