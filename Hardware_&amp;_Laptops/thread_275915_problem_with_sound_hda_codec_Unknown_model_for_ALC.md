---
title: "problem with sound ::hda_codec: Unknown model for ALC861"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by saganga on 2006-10-12
Hello,
On my Ausus notebook, sound doesn't work with Ubuntu Dapper; I saw on my syslog the string "hda_codec: Unknown model for ALC861".May be I have to install a more update hda_codec ? I tried to installing the last stable "alsa" version 1.0.13, but I get the same message. Could someone help me ? Thank you

---

### Post by brightbyte on 2006-10-23
I'm having the same problem with the ICH7 chipset on an ASUS Z53J laptop ([details of my system and alsa setup]("http://http://area23.brightbyte.de/misc/alsa-trouble.txt"))

I found this  [bug report]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/44814") that indicates that the problem is solved in the very latest version of alsa (1.0.11) which I have not tried yet. The previous version (1.0.10rc3) does not work, even with the latest kernel 2.6.15-27.48.

I'll try to find a package of 1.0.11 and let you know how it goes.

---

