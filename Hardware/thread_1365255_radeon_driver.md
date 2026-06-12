---
title: "radeon driver"
date: 2009-12-27
forum: Hardware
---

### Post by u_kapaley256 on 2009-12-27
Hi,
I have ati radeon hd 4200 in my laptop and running kubuntu 9.10.
I tried installing drivers from the repository but it screwed up kwin and the window borders disappeared.
So i looked up some solution on the net and one guy was telling that i should try the drivers from the ati website which does not have my device listed !!
So i downloaded and tried radeon hd 4300 and followed the procedure to the same result i.e. window borders screwed up.
What should i do?
Should i go for the open source drivers for the ati?

Pls help.

---

### Post by u_kapaley256 on 2009-12-30
Hi,
I figured it out
I downloaded the proper drivers from the ati site
(I was looking into radeon drivers while mine was in 'mobility radeon')
Then i installed those drivers but to actually use them it was required to edit xorg.conf which wasn't there in karmic

So basically the solution is this :-
1)aticonfig --initial (which generated the xorg.conf)
2)reboot

Done!

---

