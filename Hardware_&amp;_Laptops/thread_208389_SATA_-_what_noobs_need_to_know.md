---
title: "SATA - what noobs need to know?"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by Burgresso on 2006-07-03
Ola

I'm (re)building my system and am considering using SATA harddrive(s). As a noob at Linux and someone who is not too technical when it comes to computer hardware, is there anything I should be aware of regarding SATA drives? Will they work with Ubuntu? 

Many thanks

Burgresso

---

### Post by tonyr on 2006-07-03
The short answer is yes, they will work, but there are issues to be aware of.  Here is a
thread about one experience:
[http://www.ubuntuforums.org/showthread.php?t=199963&highlight=sata+howto]("http://www.ubuntuforums.org/showthread.php?t=199963&highlight=sata+howto")

---

### Post by Burgresso on 2006-07-03
thanks tonyr - I'll take a look at that and I appreciate your response. Is portland really the center of the linux world? :)

---

### Post by Burgresso on 2006-07-03
Do you *have *to run RAID for a SATA drive, of can you just use a SATA drive "normally"?

---

### Post by tonyr on 2006-07-03
No, you do not have to use a RAID configuration.  You can use it "normally". 
Be careful if you have both SATA and PATA (older ide) devices.  If your BIOS
supports a boot choice for SATA, you probably need to have that selected in
your CMOS setup.

Linus Torvalds, father of Linux, lives at last report in Portland, OR 
(See [this]("http://en.wikipedia.org/wiki/Linus_Torvalds")), where he is a Fellow at [OSDL]("http://www.osdl.org/") (next door in Beaverton, OR).

---

### Post by Burgresso on 2006-07-03
Thanks again tonyr, and also for the tidbits about portland!

---

