---
title: "Dell 1390 WLAN Broadcom 4311  ndiswrapper &amp; 9.04 upgrade"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Grendel336 on 2009-04-25
Has anybody with a Dell Inspiron E1505 or similar laptop that uses the 1340 wlan wireless card upgraded to Jaunty? 

I'd like to know what the experience was regarding the wireless card and ndiswrapper. 

Sorry if this has already been addressed somewhere. I searched and found nothing. 

I am currently happy with Intrepid so the upgrade can wait if there are problems with the wireless card that Dell installs on the E1505 machines. 


Thanks

---

### Post by StuartN on 2009-04-25
> **Grendel336 said:**
> Has anybody with a Dell Inspiron E1505 or similar laptop that uses the 1340 wlan wireless card upgraded to Jaunty?

I haven't upgraded (because of the Radeon graphics) but I have run the Live CD on my Dell Inspiron 1501. The Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) was recognized and I was offered either b43 or wl in Hardware Drivers. I tried the wl driver with a WPA access point and it worked fine. I have not needed ndiswrapper.

---

### Post by Grendel336 on 2009-04-25
Thanks,

When I installed 8.04, and then again when I installed 8.10 I had to run through this tutorial to get connected to internet through my wireless. 

[http://ubuntuforums.org/showthread.php?t=760568&highlight=Dell+1390+WLAN]("http://ubuntuforums.org/showthread.php?t=760568&highlight=Dell+1390+WLAN") <--- clicky

I imagine if you are just running the live CD your old settings are still functioning in the background. 

Or am I mistaken? 

I just wonder if I'm gonna have to run through a similar tutorial to get internet access after I upgrade to 9.04

---

### Post by StuartN on 2009-04-26
> **Grendel336 said:**
> I imagine if you are just running the live CD your old settings are still functioning in the background. 

Or am I mistaken?

Under the Live CD you are running completely off the CD, your existing partitions are not mounted and your old settings are not applied. I found the Live CD gave me a choice of 2 proprietary hardware driver for the Broadcom wireless and it worked straight off out of the box. I had to go through some weird steps to get wireless working in earlier distributions, but 9.04 seems to have it fully sorted for my card.

---

### Post by Grendel336 on 2009-04-26
> **StuartN said:**
> Under the Live CD you are running completely off the CD, your existing partitions are not mounted and your old settings are not applied. I found the Live CD gave me a choice of 2 proprietary hardware driver for the Broadcom wireless and it worked straight off out of the box. I had to go through some weird steps to get wireless working in earlier distributions, but 9.04 seems to have it fully sorted for my card.

Sweet. Thanks for the return response. Perhaps I shall try it.

---

### Post by Grendel336 on 2009-04-30
I did a complete 9.04 install from CD, and it all worked wonderfully. 

Had a few things to sort out, but overall I could get up and running on my own in less than 30 minutes. That's a huge accomplishment from somebody who's as useless as I am with working in the Linux environment. 


Any issues with the wifi and Dell wireless card was fixed with this upgrade.

---

