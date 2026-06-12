---
title: "Suspend/Hibernate with ATI Mobility Radeon HD 4650"
date: 2009-11-23
forum: Hardware
---

### Post by alperyilmaz on 2009-11-23
Anybody had luck with suspend working properly with ATI Mobility Radeon HD 4650 in Ubuntu 9.10 (64-bit) ?

I installed ATI Catalyst 9.11 from ATI website. But, as of now, machine suspends but cannot wake up..

I end up with blank screen. Mouse is responsive. I can change to virtual terminal and I see the following error printing in an endless loop:

> EXT4-fs error (device sda5): ext4_find_entry: reading directory #81922 offset 0

(/dev/sda5 is root partition, /dev/sda6 is home partition)

---

### Post by alperyilmaz on 2009-12-08
bump!

no solution for this?

update: I tried [this]("http://ubuntuforums.org/showthread.php?t=1331522&page=3") workaround but it didn't help.

update2: [This]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver") page describes a solution related to FGLRX and ATI interference, but i'm not sure if it applies to me. Since I didn't switch from fglrx to ati in past. But, fglrx is installed and running in my system, shouldn't it?

---

### Post by frumple on 2009-12-16
Just to inform, I've tried suspend on Sabayon 5.0 on a notebook with the Radeon Mobility 4650 and it worked perfectly. 

I don't have Ubuntu installed right now, but I hope this information helps you some how. 

Regards,
Eduardo

---

### Post by alperyilmaz on 2009-12-18
Hi Eduardo,

are you using Catalyst drivers?

---

