---
title: "Adding second SATA drive to 10.04 not recognized"
date: 2013-03-04
forum: Hardware
---

### Post by beelatch on 2013-03-04
I suppose this goes here and not the "upgrades" section since it is hardware related. I added a Seagate 1TB SATA drive to my existing 10.04 LTS AMD64 system with a 400GB WD SATA drive. The BIOS on the Biostar MB sees the second drive but lshw doesn't:

bruce@bruce-linux:~$ sudo lshw -C disk
[sudo] password for bruce: 
  *-disk:0                
       description: ATA Disk
       product: WDC WD4000AAJS-0
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 12.0
       serial: WD-WCAS80932509
       size: 372GiB (400GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000d650c
  *-cdrom
       description: DVD-RAM writer
       product: CD/DVDW SH-S182M
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/SNDMUSIC
       version: SB04
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/SNDMUSIC
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted



Neither does fdisk of course. I checked the /etc/modprobe.d blacklist files but I don't see anything apparent. Am I missing something?

---

### Post by beelatch on 2013-03-07
Anyone???? Don't tell me I found a new unresolvable problem.

---

### Post by gordintoronto on 2013-03-07
Have you formatted the new drive with Gparted?

---

### Post by dcstar on 2013-03-08
Check the BIOS settings for ACHI/IDE/RAID mode for the SATA port you have it connected to.

---

