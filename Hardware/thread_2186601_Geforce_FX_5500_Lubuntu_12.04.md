---
title: "Geforce FX 5500 Lubuntu 12.04"
date: 2013-11-08
forum: Hardware
---

### Post by bazsound on 2013-11-08
Yesterday i installed lubuntu 13.04 on an old machine, and to my delight it transformed an old machine (shuttle x pc - AMD XP 2400 2ghz with 1.5gb ram) from a sluggish unresponsive machine into something very usuable, not only able to play DVD's (that it could not do  in windows without stuttering) but quite happy at doing more than 1 thing at the same time. AND it would boot up quick, windows would log in and spend 5 minutes loading **** for no reason

anyway, i realised that the legacy card after trying multiple nvidia drivers was just not going to work. The best i got was the NVIDIA logo before logon, however it would stay up for 10 seconds screen go blank and the PC would freeze. the last effort was 173 drivers direct from nviidia, this did not freeze the pc however after the logo, all i got wasw a blank screen, while the keyboard would respond, the screen stayed blank.

Im pretty sure that legacy drivers do not work correctly with recent xorg, but information is conflicting by googling.

So im trying 12.04, but again information is conflicting and quite sparse.

Im now working through an install of 12.04 to try and get nvidia to work, but am i waisting my time, will i have to downgrade xorg?

I need the drivers so i can use xbmc, as this pc is going to be perfect for a media centre, xbmc needs open gl.

should i just go back another version to 11.10?

---

### Post by mörgæs on 2013-11-08
How does it work in a plain vanilla installation of Lubuntu 13.10 without restricted drivers?

---

### Post by bazsound on 2013-11-08
it works very well using the open source driver. The machine is like a complelty different machine.

However XBMC media centre will not run without opengl acceleration.

everything else works as expected

---

### Post by mörgæs on 2013-11-08
So far, so good. 
What happens when adding restricted drivers to 13.10?

---

### Post by Revhead on 2013-11-09
I had problems installing the latest version of Ubuntu on an old P4 2.6Ghz box with an FX 5200 card.
I dropped back to 10.04 LTS, it allowed me to install proprietary Nvidia drivers (version 173) and it works like a charm. Give it a try.

---

### Post by mörgæs on 2013-11-10
10.04 is out of support, and though it might perform well it's vulnerable to an attack (and has been so for more than half a year). There are better solutions, for example Xubuntu 12.04.

---

