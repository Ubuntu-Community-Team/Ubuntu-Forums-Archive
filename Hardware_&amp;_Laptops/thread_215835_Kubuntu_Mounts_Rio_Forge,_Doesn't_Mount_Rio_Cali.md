---
title: "Kubuntu Mounts Rio Forge, Doesn't Mount Rio Cali"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by wyth on 2006-07-14
Okay, here goes:

I'm running Kubuntu Dapper 6.06 (KDE 3.5.3, kernel 2.6.15-26-k7). I have two Rio mp3 players here, one Rio Forge and one Rio Cali. When I plug in the Forge, it's detected right away as a USB device and I can transfer files. When I plug in the Cali... nothing.

The dmesg command shows "usb 5-1.4: new full speed USB device using ehci_hcd and address 7," so it's being detected.

The lsusb command in /sbin shows "Bus 005 Device 007: ID 045a:500f SONICblue, Inc." So it's detected there.

And sudo mount -a doesn't bring it up.

My fstab reads:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdd1 /media/hdd1 vfat iocharset=utf8,umask=000 0 0
/dev/hdd2 / reiserfs notail 0 1
/dev/hdd6 /home reiserfs defaults 0 2
/dev/hdd5 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

I'm hoping not to have to boot into windows just to get podcasts and mp3's onto the player, but that's where I'm at right now. There's gotta be some voodoo I'm just not sure of at the moment.

Cheers

---

### Post by wyth on 2006-07-14
bump

---

### Post by wyth on 2006-07-15
Badabump

---

### Post by wyth on 2006-07-16
C'mon, no one has any info on this?  I know *someone* must...

---

### Post by wyth on 2006-07-19
Bump, I say, BUMP!

---

### Post by Xehoz on 2006-10-11
bump

Same thing, with Ubuntu Dapper, 2.6.15-27. Dmesg and lsusb, are the same and rioutil ([http://rioutil.sourceforge.net/](http://rioutil.sourceforge.net/))

> Attempting to open Rio and retrieve song list....
Device not found.
library tried to use method: libusb
Because, well, it doesn't show up as a mounted device.

Anyone has a clue?

---

### Post by taddy_porter on 2006-11-25
You have to run rioutil as root.

---

### Post by rogue_ronin on 2006-12-10
Red button Cali's are not Mass Storage devices, only black button ones are.  Forges are all Mass Storage.

m a r

---

