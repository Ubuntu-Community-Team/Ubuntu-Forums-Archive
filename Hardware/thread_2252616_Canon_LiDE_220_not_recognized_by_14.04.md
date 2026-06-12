---
title: "Canon LiDE 220 not recognized by 14.04"
date: 2014-11-13
forum: Hardware
---

### Post by cathect2 on 2014-11-13
Anyone get a Canon LiDE 220 to work with Ubuntu? I can't get it to even recognize the scanner. Any tips appreciated!

I get the following err or after issuing sane-find-scanner:
> 
found USB scanner (vendor=0x04a9 [Canon], product=0x190f [CanoScan]) at libusb:002:004
could not fetch string descriptor: Pipe error
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.




---

### Post by rafe101 on 2015-02-07
Hi. did you ever resolve this? I just picked up the same scanner because I saw it was supported by SANE, but I'm getting the exact same messages. It's driving me inSANE.

---

### Post by pdc on 2015-02-07
Hi rafe101; sorry to hear of your problems; I saw that you said > because I saw it was supported by SANE but when I look on sane, I can't see the 220 listed at all; much less supported [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)

it came up on a Mint forum [http://forums.linuxmint.com/viewtopic.php?f=51&t=186720&p=966854&hilit=canon+lide#p966854](http://forums.linuxmint.com/viewtopic.php?f=51&t=186720&p=966854&hilit=canon+lide#p966854)

the ID of the device seems to be 04a9:190f

_________________

an option is to purchase Vuescan [http://www.hamrick.com/vuescan/canon_lide_220.html](http://www.hamrick.com/vuescan/canon_lide_220.html) ................by keeping this very capable programme going, these folks put food on the table for themselves; as we all do in some way; we have installed it, and it is a very capable programme;

the sane work is all volunteers; in their spare time;

---

### Post by rafe101 on 2015-02-09
I guess I did some poor research. I saw messages like these ( [http://ubuntuforums.org/showthread.php?t=2258489](http://ubuntuforums.org/showthread.php?t=2258489) ) that led me to believe it was ready.

According to the site you linked, that won't help me either as i's also not supported. So, what to do now&#8212;wait & hope or send it back?

---

### Post by pdc on 2015-02-09
> So, what to do now

> an option is to purchase Vuescan [http://www.hamrick.com/vuescan/canon_lide_220.html](http://www.hamrick.com/vuescan/canon_lide_220.html) ................by keeping this very capable programme going, these folks put food on the table for themselves; as we all do in some way; we have installed it, and it is a very capable programme;

the sane work is all volunteers; in their spare time; 

folks often talk of linux as free..................but it is said that it is free as in speech..................................not free as in beer...................so some folks support linux and earn their living eg Redhat [http://www.redhat.com/en](http://www.redhat.com/en)

---

### Post by rafe101 on 2015-02-10
Look.  Almost every time I've seen you comment on a thread it's been with the same message.  I don't have a problem with people shilling for a group.  I may have even bought the software if it did what I need.  But this DOES NOT.  On the page you provided it states in multiple places that the LIDE 220 does not work on Linux with that software. But I downloaded the program anyway and tried it  out runs but still DOES NOT FIND A SCANNER. 

This software is not a magic cure for all scanner problems. It is just another Frontend that needs the drivers in place to work.

---

### Post by pdc on 2015-02-10
Hi rafe; sorry to hear of your continuing problems; it must all be very irritating and exasperating

The folks at Vuescan when I look on their website would want to hear from you and help you; 

if you go here [http://www.hamrick.com/support/frequently-asked-questions/i-have-a-problem-with-vuescan-how-do-i-solve-it.html](http://www.hamrick.com/support/frequently-asked-questions/i-have-a-problem-with-vuescan-how-do-i-solve-it.html) they urge you to get in contact with them and help them resolve this for you.

---

### Post by pdc on 2015-02-26
Hi rafe; if you are following this thread; or the sane-development list, I see the developers are encouraged at the progress they are making to have the LiDE supported by SANE; they now think weeks so that will be great for those with such high-spec and excellent scanners;

---

