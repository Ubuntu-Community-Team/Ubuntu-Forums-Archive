---
title: "New machine weird consol error on boot."
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by twistedgamer on 2009-03-27
I'm attempting to install Ubuntu 8.10 on a new PC.

Hardware is

MB: ASUS M2A-VM
HD: WD 120GB
CD: Generic CD-Rom
Proc: AMD Athon 64 3500
Mem: Crucial 1GB, 240-pin DIMM, DDR2 PC2-6400 (x2)
Vid: On board or ATI x1650

I've tried changing between sata and ide drive, changed DVD drives, power cables for the drives, data cables for the drives. 

I've downloaded and burned (from different mirrors and different pc's) fresh ISO's. I've ran memtest for 2 days straight (forgot the machine was even running it). Ran boot and nuke on both drives. 

And I get one of two errors. One is text about a boot failure and the other is a weird console window that pops up during Ubuntu boot from CD with a bunch of data.

Attached is picture of the console displayed on the monitor.

---

### Post by upchucky on 2009-03-27
the boot error would be the easier one to fix, but i suggest using 8.04 instead of 8.10. 8.10 is not a long term supported release and has issues with 3d graphics.

while you are at it, i also suggest using the alternate cd for installing, it makes setting up graphics easier, and is forgiving when trying to detect some hardware inconsistencies.

---

### Post by twistedgamer on 2009-03-27
Well the boot error message is
"isolinux disk error 80, aux = 4200, drive 9F"

---

### Post by upchucky on 2009-03-27
if you can get a desktop using the live cd do this.

download this

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh
```


post the results here, you may be able to figure what is wrong yourself and there are plenty of people here that can tell you exactly what to do when they see the drive setup you have.

---

### Post by twistedgamer on 2009-03-27
Drive setup is a single hard drive.

It's basically factory fresh because of Boot and Nuke I ran.

As for booting off the CD, that's what I've been trying to do that's where the two error messages are coming from.

---

