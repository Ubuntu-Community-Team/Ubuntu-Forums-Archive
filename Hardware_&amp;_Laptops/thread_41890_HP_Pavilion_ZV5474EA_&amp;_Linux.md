---
title: "HP Pavilion ZV5474EA &amp; Linux?"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by nocturn on 2005-06-15
Sorry for asking again...

I'm considering buying this portable (or an Acer I mentioned in another thread).
Does anyone have this machine?  How well does it work with Ubuntu?

Any quirks I should know about?

Thanks

---

### Post by nocturn on 2005-06-16
OK, I found some comments on other zv5000 machines.  It should work rather well with one big obstacle...

The PCMCIA slot seems to have trouble under Linux which can be possibly fixed with some weird setting, but if you are wrong it can cause damage to the system.  Sigh, the quest for a Laptop that will run Linux well is hard...

---

### Post by nomad311 on 2005-07-26
did you end up gettin that laptop?

ive had quite a few problems with mine its either a zv52xx or zv5410 ...the box said 5410 but the info on ms help center says zv52xx

not important but the probs ive had so far wit ubuntu (installed last night LOL):
-X wont start when i try to upgrade to the nvidia driver
-havent setup wireless ...but i kow how (had gentoo on here till yesterday and i had to abondon it do to an error im to inexperienced to fix) caue i ordered a orinoco 802.11a/b/g gold !! should be fun!
-it froze at hotplugging once ...i did a hard reboot and it acted like nothing happended ...weird ARG: it wssnt till now that i membered reading somewhere that hitting the ~ key unfreezes it ...the guy said it worked for him once ... but he cant verify that it actually did nething
-i havent setup xmms to run on esd but im hopin these other guys will tell me how they did it ...im fine with alsa for now though
-also i did add those lines to my pcmcia script but havent used it yet so dunno if ne damage has been done lol

hows it goin for you ...can you help me out ne ...or can i helo u out ne HA
-nomad311

---

### Post by nocturn on 2005-08-01
[QUOTE=nomad311]did you end up gettin that laptop?

ive had quite a few problems with mine its either a zv52xx or zv5410 ...the box said 5410 but the info on ms help center says zv52xx

not important but the probs ive had so far wit ubuntu (installed last night LOL):
-X wont start when i try to upgrade to the nvidia driver
-havent setup wireless ...but i kow how (had gentoo on here till yesterday and i had to abondon it do to an error im to inexperienced to fix) caue i ordered a orinoco 802.11a/b/g gold !! should be fun!
-it froze at hotplugging once ...i did a hard reboot and it acted like nothing happended ...weird ARG: it wssnt till now that i membered reading somewhere that hitting the ~ key unfreezes it ...the guy said it worked for him once ... but he cant verify that it actually did nething
-i havent setup xmms to run on esd but im hopin these other guys will tell me how they did it ...im fine with alsa for now though
-also i did add those lines to my pcmcia script but havent used it yet so dunno if ne damage has been done lol

hows it goin for you ...can you help me out ne ...or can i helo u out ne HA
-nomad311[/QUOTE]

Sorry for replying this late (I was on holiday).
I got the laptop and it installed perfectly.

The nvidia drivers didn't work at first, but you need to add 'NVreg_Mobile=0'  as a parameter to the nvidia kernel module.

Wireless worked flawless with ndiswrapper.

Things that are not working
- supend/hibernate.  It does switch of on hibernate, but crashes on power on.
- The touchpad and USB mouse have quirks (have to switch to a vc and back to get mouse to click).
- the backlight of the screen does not turn off, even though dpms is enabled.

I think that's it, the rest is working very well.

---

