---
title: "Catalyst 12.6 Underscan"
date: 2012-07-02
forum: Hardware
---

### Post by pyro226 on 2012-07-02
I was having problems with my Radeon 6850 underscaning each boot (it wouldn't save underscan setting).  Each time I rebooted the computer it would return to black bars and underscanned.  I didn't find much even with a lot of searching.  

Then I found [http://www.rage3d.com/board/showthread.php?t=33991741](http://www.rage3d.com/board/showthread.php?t=33991741)

The solution was the optional step after step 9 in the guide:
(Optional 9b. if you have black bars normally, disable underscan (always after lightdm has stopped): sudo aticonfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0)

Posting it here in case anyone else has this problem.

---

### Post by daisycutter469 on 2012-12-03
+ 5mo later and this solution worked for me, thanks.

Ubuntu 12.10
AMD/Ati BETA drivers (12.11)
Radeon HD6750

---

### Post by sean-fitzpatrick on 2013-08-22
Thanks for posting! The same fix works for Catalyst 13.4 in Ubuntu 13.04. Perhaps the better question is: who would have thought that this should not be the default behaviour, and if anyone happens to know them, could you give them a good shake?

---

