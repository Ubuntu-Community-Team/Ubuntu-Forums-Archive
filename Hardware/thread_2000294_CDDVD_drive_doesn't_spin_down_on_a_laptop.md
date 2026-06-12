---
title: "CD/DVD drive doesn't spin down on a laptop"
date: 2012-06-09
forum: Hardware
---

### Post by the_mouse on 2012-06-09
Hey guys, I'm using Kubuntu 11.04 on a HP Probook 4530 laptop and just noticed that a unused DVD in the dvd-rom is constantly spinning at low speed, even if not being used for hours. I find that really uneccessary and I tried:

$ sudo hdparm -B 127 -S 24 /dev/sr0

/dev/dvdrw:
 setting standby to 24 (2 minutes)


with sr0 being my dvd drive:

$ sudo lshw -class disk
  *-cdrom
       description: DVD-RAM writer
       product: DVD A  DS8A5LH
       vendor: hp
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1H68
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc


but setting the -S param in hdparam had no effect. 
Do you guys have an idea how to set some spindown time, so the drive won't spin forever when a disc is present?

Thanks,
Dimitar

---

