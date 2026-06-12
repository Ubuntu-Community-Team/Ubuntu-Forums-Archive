---
title: "pccard modem works on 5.10, not on 6.06"
date: 2006-08-15
forum: Hardware &amp; Laptops
---

### Post by killfire on 2006-08-15
I'm not sure if this should be in networking, but since pccards are exclusive to laptops, it seems more appropriate.

I have an old laptop, a thinkpad a20m (march 2000), which works very well. I had on it ubuntu 5.10, but I just got a hold of xubuntu 6.06, which I installed and like very much. However, the modem no longer works. It is a pccard modem, but not a winmodem I do not think, because it has worked forever, and up until relatively recently it seemed only real modems worked at all. It is a 3com one, the exact model I'm not sure because it is in the computer and I am using it right now. If it is really important, I can check later. The way I am online is with the livecd of 5.10 that I have. 

On 6.06, it recognizes the pccard, but in startup it assigns it the device /dev/ttyLsomething0, not a /dev/ttyS0 or 123. it also mentions some stuff about lucent modems, which this is not. I don't know why 6.06 is falsely identifying this modem, but as a result, it does not work. if I unplug it and plug it in it identifies as /dev/ttyS2 in dmesg, but it still will not work, using network-admin to dialup. 

Oh, also, I tried the ubuntu 6.06 desktop cd, and the problem is the exact same as with xubuntu, so that is not the problem... 

the only thing I can think of, is that it seems that pcmcia-cs has been superceded by pcmciautils, and possibly this change is causing this problem.

I welcome any advice.

---

### Post by killfire on 2006-08-18
No responses? What happened to Ubuntu just working? At this rate I might just switch back to Gentoo....

---

