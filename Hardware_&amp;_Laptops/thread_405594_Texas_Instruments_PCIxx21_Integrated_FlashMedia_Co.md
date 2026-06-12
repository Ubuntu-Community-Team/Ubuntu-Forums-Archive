---
title: "Texas Instruments PCIxx21 Integrated FlashMedia Controller"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by JoaoMachado on 2007-04-09
I have upgraded to fiesty and my media card reader seems to have an issue with SD cards and reading them. System is an HP ZD8000 series notebook. When I insert the SD card, the indicator light comes on for two seconds then off then on for one second then blank for about two seconds then starts the whole thin over.

Running dmesg I get:
```
[ 1927.172989] end_request: I/O error, dev mmcblk0, sector 102
[ 1927.173005] mmcblk0: error 1 sending read/write command
[ 1927.173011] end_request: I/O error, dev mmcblk0, sector 103
[ 1927.173027] mmcblk0: error 1 sending read/write command
[ 1927.173032] end_request: I/O error, dev mmcblk0, sector 104
```

but if I run dmesg right after I install the card I get:
```
[ 2091.341223] tifm_7xx1: sd card detected in socket 3
[ 2091.548831] mmcblk0: mmc3:bfc6 SD128 123008KiB 
[ 2091.548889]  mmcblk0: p1
```

fdisk output is :
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9447    75882996   83  Linux
/dev/sda2            9448        9729     2265165    5  Extended
/dev/sda5            9448        9729     2265133+  82  Linux swap / Solaris
joao@ZD8000:~$ 
```

Obviously it is being recognized (sort of), but nothing mounts, I tried another SD card and it does the same thing? Any ideas would be greatly appreciated.

---

### Post by JoaoMachado on 2007-04-11
bump...

---

### Post by thegnark on 2007-04-17
adding a "me too" to this

in fact, my logs are completely filling up in /var/log with the errors in kern.log, debug, and syslog

---

### Post by JoaoMachado on 2007-04-20
thegnark, did you do an upgrade from 6.10 or a fresh install?

---

### Post by brien on 2007-04-24
i'm having the same (or at least, very similar) problem. this is a fresh feisty install. dmesg after inserting a card shows:
> 
[16937.240000] tifm_7xx1: sd card detected in socket 3
[16937.348000] mmcblk0: mmc3:f77a SD064 60544KiB 
[16937.348000]  mmcblk0: p1
[16937.348000]  mmcblk0: p1 exceeds device capacity

---

### Post by brien on 2007-04-24
just tried the setpci mentioned in this thread and it worked right away for me:
[http://ubuntuforums.org/showthread.php?t=315497](http://ubuntuforums.org/showthread.php?t=315497)

---

### Post by macogw on 2007-04-24
The tifm modules are broken in Feisty.  Go here:
[http://ubuntuforums.org/showthread.php?p=2520594](http://ubuntuforums.org/showthread.php?p=2520594) to install updated ones.  And this one's not even a hack, it's more of a patch.

---

### Post by JoaoMachado on 2007-04-24
This worked perfectly, much appreciated...

Also, I had upgraded from an Edgy fresh install to Fiesty beta, I noticed Edgy Kernel was still on my Grub list and it also worked just fine. (2.6.17-10-generic) \\:D/

---

### Post by RealG187 on 2008-05-05
I have the PCIxx12 (Acer Aspire 9410)

Could I get it working, I am most likely to install 8.04

"Texas Instruments PCIxx 12 Integrated Flash Media Controller" is what I got

---

### Post by JoaoMachado on 2008-05-06
> **RealG187 said:**
> I have the PCIxx12 (Acer Aspire 9410)

Could I get it working, I am most likely to install 8.04

"Texas Instruments PCIxx 12 Integrated Flash Media Controller" is what I got

I could not tell you, I sold my HP last year for a set of golf clubs :(

---

