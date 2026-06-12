---
title: "Vizio tv used as a monitior will it work with ubuntu?"
date: 2009-11-27
forum: Hardware
---

### Post by psychovampire85 on 2009-11-27
I have a vizio tv from wal-mart and i am getting ready to install ubuntu on a computer i got from college. I am wondering since i have it hooked up to the tv if ubuntu will work alright with it?

---

### Post by paulisdead on 2009-11-27
You've not given any model, specs or what type of input you want to use on the TV.  It should detect it just fine.  HDMI and S-Video have autodetected on TVs just fine for me, but I always use nvidia cards on those systems.

---

### Post by efflandt on 2009-11-27
It depends how you connect it.  DVI, HDMI, or DVI to HDMI should recognize it automatically.  For VGA it depends whether Linux recognizes it from plug and play and whether X figures out suitable mode(s)

I have an old 27" HDTV Ready Apex LCD natively 1280x720, and it just says it supports PC video modes up to 1280x1024.  With some old computers I was resurecting, the default video mode in X was an odd 4:3 mode in the 11xx by 8xx range that worked, but was stretched.  X offered an alternate 1360x768 widescreen mode which is close enough to the native mode of most 720p LCD's, and that worked fine even on my 1280x720 LCD.

When I plugged that 27" into my desktop with DVI and a video card that supports HDTV modes, both Linux and Windows recognized its native 1280x720 mode (real 720p).

When I connected my laptop to my 40" 1366x768 HDTV with VGA, for some reason the best X could do was a 1024x768 4:3 mode either pillar boxed, or stretched full screen.  The X 1280x720 (720p) mode was way overscanned, cutting off top, bottom and sides.  That is strange because WinXP with same laptop and display comes up with a 1360x764 mode close enough to the native mode of the display to be properly sized and very sharp.

I'll have to try my desktop with the 40" screen DVI to HDMI when I get time, to see if it comes up with the native mode of the screen.  DVI or HDMI digitally communicate more details of their capabilities with the source than VGA plug and play.

So results may vary depending upon hardware.

---

### Post by jessiebrownjr on 2009-11-27
I bought a 1080p 22inch VIZIO tv/monitor today, and it installed and resized itself correctly on Ubuntu 9.04.

I was using RGB/VGA, and tommorrow will be testing out the same thing with DVI cables. 

Id imagine if your  tv is new, and you are using 9.04, it should work!

---

