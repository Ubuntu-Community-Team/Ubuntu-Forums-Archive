---
title: "No monitor signal?"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by FadedReality on 2009-03-01
I have a: 
dell dimension 2400 
1 gig of ram
integrated video card
pentium 4 3.0Ghz
Monitor runs at 1024x768 up to 32-bit at 60hz

I have tried to install 3 different versions of ubuntu (8.10, 8.04, 7.10)

With every one on both install and just running the live cd, it will show the logo with an orange bar at the beginning as if loading. Then my monitor goes blank with a little image saying no signal. The cd seems to be accessed for a short time then the computer just sits there dead in the water.

I have tried ctrl+alt+F1 and then my monitor comes back on and I see the dos/console asking for name/pass. So it would seem that I can log into the dos/console part.

I tried changing the bios onboard memory buffer from 1MB to 8MB but still same results. 

I would like to run ubuntu but it seems I'm going to need some help. Any feedback would be appreciated.

---

### Post by Shazaam on 2009-03-01
You can try this when booting the livecd...
When the livecd screen starts that gives you choices on how to boot look for the "F6 Other Options" section (lower right). Add this to the end of the line that pops up...
```
vga=782
```
See if the livecd will completely boot up. If not, go back (after a reboot) and delete "splash" on the same line. You can also hit F4 and choose "Low graphics mode".

---

