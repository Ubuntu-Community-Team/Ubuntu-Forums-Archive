---
title: "getting old video card working"
date: 2012-08-27
forum: Hardware
---

### Post by Johoul on 2012-08-27
Hi there -

I'm hoping to revitalise my old Dell D600 laptop by switching from Xp to Ubuntu. Installed 11.10 and upgraded online to 12.04  (due to lack of processor support in 12.04 installation cd). 

It's working Ok so far, my main problem is that that the Ati Radeaon Mobility 9000 graphics card (rv250) is not installed correctly, glxgrears gives a fps of ~75.

I did manage to find a distribution where the card does work (SimplyMEPIS 7.0 - glxgears fps ~ 2000) - However, in this distribution my wireless card doesn't work. 

It would be ideal for me if I could learn something from the Mepis installation and apply it to Ubuntu to get the video card working. Unfortunately, my knowledge is limited so any advice would be greatly appreciated -

Thanks.

---

### Post by ajgreeny on 2012-08-27
> **Johoul said:**
> Hi there -

I'm hoping to revitalise my old Dell D600 laptop by switching from Xp to Ubuntu. Installed 11.10 and upgraded online to 12.04  (due to lack of processor support in 12.04 installation cd). 

It's working Ok so far, my main problem is that that the Ati Radeaon Mobility 9000 graphics card (rv250) is not installed correctly, glxgrears gives a fps of ~75.

I did manage to find a distribution where the card does work (SimplyMEPIS 7.0 - glxgears fps ~ 2000) - However, in this distribution my wireless card doesn't work. 

It would be ideal for me if I could learn something from the Mepis installation and apply it to Ubuntu to get the video card working. Unfortunately, my knowledge is limited so any advice would be greatly appreciated -

Thanks.
It is not worth trusting glxgears as a benchmark of how badly or well your graphics card and driver are working, and I imagine that if you are getting a reasonable display there is no problem at all with the card.  It is, as you say, an old integrated ATI card, often found in laptops of the early 2000s, and I think that the glxgears output in 12.04 says that the fps rate it shows will be the same as the display sync rate, ie 75fps.

So forget about your "problem" and if you are seeing a good display, live with it. There is absolutely nothing you can do better with it, as there are no proprietary drivers for these old ATI cards any more; the open source radeon driver is your only choice.

Mepis probably uses an older version of glxgears that does not show fps in the same way as Ubuntu, and if you were running an older version of Ubuntu, eg 10.04, you would also see a higher fps rate.

---

### Post by Johoul on 2012-09-06
Thanks ajgreeny - I just saw your reply now (need to check my notifications!), I had just about reached the same conclusion. I copped that glxgears was just giving me my refresh rate and found a way to relax this constraint, my frame rate improved up to a few hundred and I guess I'll have to be happy with this. 

Anyways, the machine is working quite well overall, very quick to boot-up / shut-down / suspend / resume which is very nice in comparison to my XP which was really slow. The one annoyance for me is flash playback which is not nearly as good as it was on XP - I've followed the advice on plenty of forums about this but none of the tricks gave me much improvement - any novel workarounds  greatly appreciated!

---

### Post by Epodx64 on 2012-09-07
You might want to consider switching to either Xubuntu or Lubuntu for that machine (neither require 3D acceleration) and they ship without the pae kernel so you could do a clean installation of 12.04.1 as for flash support well honestly it pretty much sucks infact adobe isnt even supporting Linux anymore the last update was the last update hopefully HTML5 comes into it's own sooner rather then later I imagine Mac users are hoping for the same thing since flash support is poor on macs as well.

---

### Post by Johoul on 2012-09-08
Thanks Epodx64, I have been using Lubuntu for the last few weeks (installed on top of my Ubuntu that was upgraded from 11.10 because of the pae). Generally there's a noticible improvement over Ubuntu but flash performance is still pretty awful. I haven't tried Xubuntu yet (I didn't realise that pae is not a requirement) will give it a go in the next few days on a separate partition just to see. I share your hopes for html5, will probably take a long time before all of the flash content is replaced I guess -

---

