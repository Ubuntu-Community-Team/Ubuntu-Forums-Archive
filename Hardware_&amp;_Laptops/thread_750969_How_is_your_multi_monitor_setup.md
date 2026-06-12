---
title: "How is your multi monitor setup?"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by Kiri on 2008-04-10
For those who have a multi monitor setup, how have you got it setup and what did you need to get it going?
Also, are you able to switch setups fairly easily or is it pretty much just set how it is?


For me, I am running my laptop display and external LCD in twinview using the nvidia-settings (nvidia restricted drivers)


It works, but I cannot find a way to switch between displays (ie: toggle only laptop, twinview laptop + external LCD, LCD + TV, etc) without spending several minutes each time going through the nvidia settings, saving the changes to xorg.conf and restarting X. 
For me clicking the Apply button in nvidia-settings never works correctly, and either messes up the displays, or crashes, or something else bad. 

Just wondering if anyone out there has their setup running so they can switch between displays or configurations easily and hassle-freely.

---

### Post by chewearn on 2008-04-11
You should keep multiple copies of xorg.conf.  E.g. xorg.conf.twinview, or xorg.conf.single.  Add the appropriate "gksudo cp xorg.conf.twinview xorg.conf" to a panel launcher.

---

