---
title: "Flickering on external monitor on intel 915"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by RushingMonkey on 2007-10-22
Hi everybody :)

I've got this old Acer Aspire Laptop equipped with an Intel graphic card (Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller); unfortunately, the built-in LCD panel is kinda broken, so I've decided to plug in an external monitor, which is a Samsung Syncmaster 931bw.

I'm using the "intel" driver, and I've got two problems: the Samsung monitor works correctly but it seems pretty "fuzzy". can't explain better in english sorry :( it just seems like little horizontal "waves" are crossing it from bottom to top. I verified the horyzontal and vertical refresh ranges on Samsung websites, and they're correctly set up in xorg.conf (also automatically detected!).

the other problem is that the built-in LCD of the laptop (which, as said, is kinda ****** up) is not turned off for some reason. also I can't turn it off from the screen applet in system => administration. ok, this is not really dramatic, but I was wondering if this is making for extra work for the video card, thus causing the problem on the external monitor?

on a side note, if I use the "i810" driver, the built-in monitor is correctly turned off when an external monitor is plugged in. too bad I can't set up a decent screen resolution with this driver -_- (I've researched in the community docs and the problems seems already documented, the solution being shifting to the new "intel" driver).

thanks in advance :)

---

### Post by RushingMonkey on 2007-10-24
no solutions? :(
I guess I'll wait for an upgrade of the intel drivers then, since they're described as "experimental".
btw I've also noticed a little problem with totem, just before it starts up the screen goes black for a split second, as he's trying to detect it.

---

### Post by silvari on 2008-01-14
if you're using the i810 driver, you can get the resolution you're looking for by also using the '915resolution' package. details here:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

