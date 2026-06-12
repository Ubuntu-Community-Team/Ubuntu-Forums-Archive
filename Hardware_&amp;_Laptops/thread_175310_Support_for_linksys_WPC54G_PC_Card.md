---
title: "Support for linksys WPC54G PC Card"
date: 2006-05-13
forum: Hardware &amp; Laptops
---

### Post by fredrik_human on 2006-05-13
Hi, i have a netgear PC Card, made in china, for my laptop and i cannot make it work with Ubuntu in spite of all the posts here on the matter. Since i'm replacing my netgear router, i'm thinking about replacing the Pc Card aswell. I'm looking at a linksys WPC54G and i wonder if that one is supported.

Anyone who knows, or have even got one working under ubuntu? I'm really sick of windows crashing all the time and the wireless issue is really the only thing holding me back from performing a "format C:, goodbye windows" today.

Regards Fredrik,Sweden

---

### Post by ivansv on 2006-05-13
i use the wrt54g router and the wpc54g card in breezy and they work well using ndiswrapper and wep encryption. download ndiswrapper-utils using apt-get install ndiswrapper-utils, and use the LSBCMNDS.inf driver from your linksys cd.
then configure using networking or from the cli using iwconfig, edit /etc/network/interfaces and it will be there when you boot up. good luck.

---

### Post by fredrik_human on 2006-05-13
Thank you, i'll try that, would be nice if it worked for me too, guess i will see when i get the gear.

---

### Post by lwr on 2006-05-14
Hi,
I've got the same card and have tried intsalling the various .inf files using ndiswrapper, but when i check them using ndiswrapper -l, it says that it's invalid. I've tried lsbcmnds.inf, lsmvnds.inf and lstinds.inf, but none of them work and i can't see any other .inf files on the cd. Any ideas? I'm pretty new to Ubuntu and linux in general, so please keep things simple.

Thanks

---

### Post by Audiophiliac on 2006-05-15
(wrong post)

---

