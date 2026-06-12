---
title: "cannot mount or see external hard drive"
date: 2009-12-09
forum: Hardware
---

### Post by pmcginley on 2009-12-09
i have a fat32 formatted western digital mybook 1TB external hard drive, relatively new (i've been using it about a month now) which i can no longer see in nautilus nor via fdisk -l. it's just gone. i got one error that said it couldn't mount the volume, and then it vanished. it does not reappear after rebooting. i booted in my windows partition, and it decided it was an 'unrecognisable usb device.'  is it hopeless?

---

### Post by adaucourt on 2009-12-09
> **pmcginley said:**
> i have a fat32 formatted western digital mybook 1TB external hard drive, relatively new (i've been using it about a month now) which i can no longer see in nautilus nor via fdisk -l. it's just gone. i got one error that said it couldn't mount the volume, and then it vanished. it does not reappear after rebooting. i booted in my windows partition, and it decided it was an 'unrecognisable usb device.'  is it hopeless?

Run this and post results:
```
sudo lshw -C disk
```

---

### Post by pmcginley on 2009-12-09
*-disk                  
       description: ATA Disk
       product: IC25N040ATMR04-0
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MO2O
       serial: MRG254K2E7YT7P
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00800080
  *-cdrom
       description: DVD reader
       product: UJDA750 DVD/CDRW
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.51
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc

no sign of it...

---

### Post by adaucourt on 2009-12-09
> **pmcginley said:**
> *-disk                  
       description: ATA Disk
       product: IC25N040ATMR04-0
       vendor: Hitachi
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MO2O
       serial: MRG254K2E7YT7P
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00800080
  *-cdrom
       description: DVD reader
       product: UJDA750 DVD/CDRW
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.51
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc

no sign of it...

Doesn't look good my friend... You can try Hiren's Boot CD, has some good disk and recovery utilities.

---

### Post by pmcginley on 2009-12-09
ugh.  thanks, will check out hiren's...

---

### Post by pmcginley on 2009-12-09
huh.  i unplugged it for an hour and went away for my dinner.  came back, plugged it in again, and it's back, as if nothing had happened.  i rebooted several times when this first occured, to no avail, so what could have changed?  this makes me extremely uncomfortable - does that mean mean my drive is on its last legs?

---

### Post by adaucourt on 2009-12-09
> **pmcginley said:**
> huh.  i unplugged it for an hour and went away for my dinner.  came back, plugged it in again, and it's back, as if nothing had happened.  i rebooted several times when this first occured, to no avail, so what could have changed?  this makes me extremely uncomfortable - does that mean mean my drive is on its last legs?

You may want to run some disk utilities to verify health of your HD.  It can be done with the afore mentioned Hiren's or you can use a native Ubuntu tool I found in this post:
[http://ubuntuforums.org/showthread.php?t=378692](http://ubuntuforums.org/showthread.php?t=378692)

---

### Post by pmcginley on 2009-12-12
thanks big a, i'll try it out.

---

