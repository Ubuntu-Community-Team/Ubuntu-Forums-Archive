---
title: "Ubunty Jaunty 9.04  + ATI Xpress 1150 = X crashes! (not even VESA)"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by stormfrog on 2009-09-29
Ive finally managed to get Jaunty working after forcing upgrades/dist-upgrades that first installed with a zillion errors.

No I have one problem left:

When I boot up my system and X11 loads screen is distorted, sometimes I can see two "Ubuntu boot" animations next to each other. Part of the screen is distorted. Sometimes I see parts of the Jaunty background.

I have a ATI Xpress 1150 card. It worked really great in 8.10 - I ran with some really heavy compiz effects and graphics was still blazing fast.

Ive tried all mu old xconfs, none work. I cant even start X with xconf.failsafe !!!!

BUT for some reason I can run Live CD with no problem. Graphics a bit dull but I dont give a crap about that. I just want a working system so I can continue my work.

Any ideas??

As I said, I dont need compiz. I just need gui!

---

### Post by Mark Phelps on 2009-09-30
ATI/AMD discontinued support for your card, and lots of others, months ago; so, there is no restricted driver available for your card that works with Ubuntu 9.04 -- period.

Could be that one of the "zillion errors" you encountered was due to the presence of fglrx drivers from 8.10 -- which will NOT work at all in 9.04.

You will need to remove the restricted drivers and run using the default open source drivers -- and you will lose 3D acceleration in the process.  Sorry, but there is no alternative with your card and Ubuntu 9.04 other than the open source drivers.

If you open the link below and scroll down to the Removing the proprietary driver section, you will see how to do it:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

