---
title: "Another Busy Box Error"
date: 2008-10-18
forum: General Help
---

### Post by M ythic_One28 on 2008-10-18
Like many others I have done a seemingly successful Inside-Windows(Vista 32bit) installation of Ubuntu 8.04 (64bit), but the OS is only able to load into the busy box command line.  

I unfortunately have no idea where to start on resolving this issue, and the threads I have read haven't yielded any results, so personalized help would be very welcome.

Here are my hardware specs, in case it helps.

Asus P5Q Deluxe motherboard (P45 chipset)
Intel Q6600 CPU
2 ATI Radeon HD4850 GPUs
2GB Sli Ready Ram
2GB Normal ram (both at 1066MHz)
2 160GB hard drives (Sata)

---

### Post by ago on 2008-10-18
please post the output of 

cat /proc/cmdline
cat /proc/partitions
cat /proc/mounts
grep err /casper.log
grep mount /casper.log

---

### Post by M ythic_One28 on 2008-10-18
:confused: Well, I assumed you were referring to the Busybox command line, so that may be the problem, but I received a "not found" error message for all the cat/... ones, and the other two resulted in a blinking _ sign. I Typed them in the given order, except for the last one, which was because I apparently lost command privileges with he second last one.

---

### Post by ago on 2008-10-20
Please note that there are whitespaces in between

cat [space] /proc/cmdline

---

### Post by Etrruugo on 2008-10-21
experience is the extract of suffering.---------------------------------------------------**  [Pet products](http://www.lovelonglong.com),     [dog bed](http://www.lovelonglong.com),   [pet supply](http://www.lovelonglong.com)    [wow power level](http://www.powerleveling-wow.com/siteMap.asp),     [WoW Power Leveling](http://www.powerleveling-wow.com),**

---

