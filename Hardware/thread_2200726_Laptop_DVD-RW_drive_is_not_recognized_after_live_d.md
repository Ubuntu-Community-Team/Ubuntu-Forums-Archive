---
title: "Laptop DVD-RW drive is not recognized after live disk install?"
date: 2014-01-20
forum: Hardware
---

### Post by mike_z2 on 2014-01-20
Hi All, 

So I have been out of the ubuntu game for the last several years and recently wanted to get back into it. I recently wiped my windows OS off my laptop and installed 12.04 on it using my dvd-rw drive. For some odd reason my dvd-rw drive does not seem to work anymore, even though I used it to install ubuntu! I can open the drive and put a dvd or cd in and the drive seems to spin up as if it were reading the disk but nothing pops up after that. Nothing shows up in the launcher/dock either (I have tried cds, dvds, and blank cds and dvds all still same response). I am kinda confused as it worked when I installed ubuntu. However, I can still live boot using the dvd-rw drive so i do not think this is a hardware issue. Also, no other software recognizes that I even have an optical drive on the laptop. (k3b and brasero insist I do not have a optical drive). So what gives?! Any help is much appreciated. My laptop is an Acer Aspire 4810 if that helps.

Long story short: I cannot read/write cds or dvds after using the dvd drive to install ubuntu 12.04.

Output from sudo lshw:

>  
  *-cdrom
       description: DVD-RAM writer
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=open


---

