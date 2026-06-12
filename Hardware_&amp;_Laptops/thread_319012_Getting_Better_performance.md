---
title: "Getting Better performance"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by macmichael01 on 2006-12-14
Does anyone have any suggestions for increasing performance in ubuntu. I am currently run on a dell latitude c600/610   intel pent III 850 384 sdram 80 gig hdd linksys wireless card.  


I disabled ipv6 and this seems to help a little. when I play music in xmms and browse the net the music jitters from time to time so I was hoping maybe some one could suggest some performance things.

maybe the video card is just a piece of crap but I don't know what it is.

---

### Post by pay on 2006-12-14
```
sudo hdparm -d 1 -A 1 -m 16 -u 1 -a 64 /dev/hda #change hda to your hard disc  
```may speed the harddrive up alittle.

---

