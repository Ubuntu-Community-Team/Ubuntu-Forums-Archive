---
title: "Problems with Graphics in battery mode"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by drascus on 2008-03-27
OK So I got this new shiny laptop form Zareason works great except one issue. When I am running from batter desktop effects seem to lag quite a bit which is kind of annoying. However when I am running on AC there is no lag. Also when I am running from battery flash Videos don't display properly they look all choppy. However when I am running on AC they are fine. I have a Nvidia Graphics card Geforce 7700 so I am wondering if it is a Glitch within in that. Any ideas?? or is this just a power saving feature that happens to be really annoying. 
Thanks for the help...

---

### Post by Rocket2DMn on 2008-03-27
I don't have an nvidia card so I can't walk you through this step by step, but that sounds like a power saving feature.  If you are running the restricted nvidia drivers, see if there are any options under
```
gksudo nvidia-settings
```  If you're NOT running the restricted drivers, maybe you should to see if that helps.

---

### Post by drascus on 2008-03-27
umm i didn't see any settings in there of consequnce but maybe its more because I don't know what I am looking for.

---

### Post by drascus on 2008-03-27
Things getting more interesting: I noticed that if I were to plug in the AC power plug and then unplug it that it would then experience no lag or choppy flash play back.... Sounds like some kind of programming glitch rather than a hardware thing or power managment thing. I don't think I can solve it with my current level of knowledge but it someone has Ideas it would be greatly appreciated.

---

### Post by Rocket2DMn on 2008-03-27
Your power settings may also have an effect on your video card, like if you scale down your processor when on battery power.
Also, it may be a BIOS setting, so you can try looking there sometime, too.

---

### Post by Whiffle on 2008-03-27
Have a look-see in /etc/acpi/battery.d/  That is where all the scripts are stored that change settings when you go to battery, well at least all the ones I know of.  There might be something nvidia related in there, I don't remember.

---

### Post by drascus on 2008-03-28
I don't see anything in that directory except for an anachron this is what it said in that script 

#! /bin/sh

# This script makes anacron jobs stop to run when the machine is
# unplugged from AC power, or suspended.

/usr/sbin/invoke-rc.d anacron stop >/dev/null   

don't know if anyone knows the meaning of this and if it has something to do with what I am experiancing.

---

### Post by Whiffle on 2008-03-28
Nah anacron is related to cron, just runs programs.  I doubt its got anything to do with your card.  Hmm.

---

### Post by drascus on 2008-03-28
I don't think it's the battery as I would expect to see other issues more severe then a graphics issue if the battery wasn't outputting enough power.

---

