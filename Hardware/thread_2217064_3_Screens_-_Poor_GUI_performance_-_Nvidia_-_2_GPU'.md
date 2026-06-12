---
title: "3 Screens - Poor GUI performance - Nvidia - 2 GPU's"
date: 2014-04-15
forum: Hardware
---

### Post by bazsound on 2014-04-15
I recently bought a card from a 2nd hand shop as i really wanted to get dual screens running again. Suspected my previous ATI radeon HD 3650 had died (and i was right)

Anyway i picked up what was supposed to be an ATI RADEON Cedar hd6450 but somehow the card was incorrecty labeled and it was actually an NVIDIA GT610. Dua screens working rreat after sorting out the correct drivers. GUI performance is fine even when running ardour DAW with lots of plugins running..

Then i thought, i have an nvidia onboard GPU. 3 SCreens!

Sure enough i changed my bios to not disabe onboard, quick play around with nvidia to get the screens the right way. And i have 3 screens. 2 running of the gt610. Both the gt610 screens are the same size 1280x1024 resolution, the third monitor on the onboard is widescreen so 1440x1280.

Now performance starts to get iffy, first screen is ok, but anything moved onto 2nd or 3rd and the redraws or super slow. Unusable.

Ardour is unusabe even with just the first screen in use and nothing on the other 2. GUI redraws are too slow and response is sluggish.

I tried all sorts of configurations, with no luck.

Whats interesting is GLX gears wil show the gears on the screens connected with the gt610 fine, but if i drag it to the screen with the onboard graphics, the gears dont show.

performance is the same wether using xinerama or not. 

Both the onboard and the gt610 use the same driver, i was using 304 on the onboard, and when i redone my system the 304 works fine with the 610.

My system isnt exactly powerfull

MSI-7309 motherboard
AMD Athon 63 X2 (2ghz)
4gb DDR-2 RAM

So maybe im just seeing the performance hit of spanning across multiple displays in software.

Is there some kind of fix, or is it just a case of bad way of doing 3 screens and id be better of running 2 of the same card or a card that can handle 3 monitors. gt610 does have an HDMI output as a 3rd port but from what ive read 1gb wont do 3 displays

---

### Post by bazsound on 2014-04-16
So ive just found out that xrandr 1.4 supports multiple gpu's however i cant find much of anything on how to set it up apart from a link to an nvidia readme which does not work.

any ideas?

---

### Post by bazsound on 2014-04-18
anyone got any ideas?

ive set up three screens again so that can have 2 screens showing same thing (for guests to see videos) and the 3rd screen for doing stuff while watching.

I have the 2 monitors on the gt610 card showing the same thing (cloned display) and the display on the onboard nvidia is xinerama desktop. runs pretty well and i can even play 2 movie files at the same time between the 2 cloned displays and the 2nd desktop screen. No lag no performance decrease.

Its only as soon as i run ardour, gui response diminishes on all displays.

---

