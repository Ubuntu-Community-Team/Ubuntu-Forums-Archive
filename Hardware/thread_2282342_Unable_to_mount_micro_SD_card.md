---
title: "Unable to mount micro SD card?"
date: 2015-06-13
forum: Hardware
---

### Post by beth3 on 2015-06-13
Hey :) I'm new to Ubuntu and running 14.04, and I'm unable to mount my micro SD card, it comes up with the following error-

 Error mounting /dev/sdd1 at /media/beth/Bob: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdd1" "/media/beth/Bob"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

There's nothing important on it so I'm not fussed about recovering data, I'd just like it to be useable again! 

Any advice?

---

### Post by MartyBuntu on 2015-06-13
Details about the microSD card and the machine you're trying to mount it on?

---

### Post by beth3 on 2015-06-13
> **MartyBuntu said:**
> Details about the microSD card and the machine you're trying to mount it on?

The SD card is a Samsung evo 64 and I'm trying to mount it on is from pcspecialist

[TABLE="class: tab_box, width: 100%, align: center"]
[TR]
[TD="class: tdb, align: right"]**Chassis & Display**[/TD]
[TD="class: td, colspan: 2, align: left"]Lafité Silver Aluminium Chassis: 13.3" Matte Full HD IPS LED (1920 x 1080)[/TD]
[/TR]
[TR]
[TD="class: tdb, align: right"]**Processor (CPU)**[/TD]
[TD="class: td, colspan: 2, align: left"]Intel® Core™ i7 Dual Core Processor i7-5500U (2.40GHz, 3.0GHz Turbo)[/TD]
[/TR]
[TR]
[TD="class: tdb, align: right"]**Memory (RAM)**[/TD]
[TD="class: td, colspan: 2, align: left"]8GB KINGSTON SODIMM DDR3 1600MHz (1 x 8GB)[/TD]
[/TR]
[TR]
[TD="class: tdb, align: right"]**Graphics Card**[/TD]
[TD="class: td, colspan: 2, align: left"]INTEL® HD GRAPHICS 5500 (Only with Intel® Core™ CPUs)[/TD]
[/TR]
[TR]
[TD="class: tdb, align: right"]**2[SUP]nd[/SUP] Graphics Card**[/TD]
[TD="class: td, colspan: 2, align: left"]NONE[/TD]
[/TR]
[TR]
[TD="class: tdb, align: right"]**Memory - Hard Disk**[/TD]
[TD="class: td, colspan: 2, align: left"]1TB WD SLIM BLUE WD10SPCX, SATA 6 Gb/s, 16MB CACHE (5400 rpm)[/TD]
[/TR]
[TR]
[TD="class: tdb, align: right"]**mSATA/M.2 SSD Drive**[/TD]
[TD="class: td, colspan: 2, align: left"]250GB Crucial MX200 M.2 2280 SSD (upto 555MB/sR | 500MB/sW)[/TD]
[/TR]
[TR]
[TD="class: tdb, align: right"]**External DVD/BLU-RAY Drive**[/TD]
[TD="class: td, colspan: 2, align: left"]NONE[/TD]
[/TR]
[TR]
[TD="class: tdb, align: right"]**Memory Card Reader**[/TD]
[TD="class: td, colspan: 2, align: left"]Integrated 2 in 1 Memory Card Reader (SD, MMC)[/TD]
[/TR]
[TR]
[TD="class: tdb, align: right"]**Sound Card**[/TD]
[TD="class: td, colspan: 2, align: left"]Realtek 2 Channel High Definition Audio + MIC/Headphone Jack[/TD]
[/TR]
[TR]
[TD="class: tdb, align: right"]**Bluetooth & Wireless**[/TD]
[TD="class: td, colspan: 2, align: left"]GIGABIT LAN & WIRELESS INTEL® AC-7265 M.2 (867Mbps, 802.11AC) + BLUETOOTH[/TD]
[/TR]
[/TABLE]

---

### Post by MartyBuntu on 2015-06-13
Are you inserting the card in the integrated card reader, or a USB card reader then plugged into a USB slot?

---

### Post by beth3 on 2015-06-13
> **MartyBuntu said:**
> Are you inserting the card in the integrated card reader, or a USB card reader then plugged into a USB slot?

I've tried both an SD card adapter and a USB adapter.

---

### Post by weatherman2 on 2015-06-13
The fact that your card is in exFat format may have something to do with it.  exFat has not been automatically supported in Ubuntu until recently - ?  Maybe it still isn't in 14.04.  In Ubuntu 12.04, I had to install exFat support on my laptop so I could read my camera's memory card.  Even after that, I cannot read an exFat with the built-in card reader, only with a USB card reader.  My internal card reader works fine for older FAT32 memory cards, and in Windows 8 it also works fine for exFat cards.

For 14.04, I'm not exactly sure what recipe might work, but here are a few options:

[http://askubuntu.com/questions/370398/how-to-get-a-drive-formatted-with-exfat-working](http://askubuntu.com/questions/370398/how-to-get-a-drive-formatted-with-exfat-working)

Unfortunately, the commands may change from release to release, and I'm not sure what the correct solution for 14.04 might be.

---

