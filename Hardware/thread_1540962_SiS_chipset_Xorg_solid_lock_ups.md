---
title: "SiS chipset Xorg solid lock ups"
date: 2010-07-28
forum: Hardware
---

### Post by ceratophyllum on 2010-07-28
I have searched and searched, finding many threads about freezes, lock ups, etc., but no solutions.

I have a compaq presario sr1320nx with integrated SiS video and Xorg freezes up at random times so that I can just move the mouse but can not click anyplace.  Ctrl-alt-backspace doesn't kill the X server, but I can log in from my laptop using ssh and kill it.

I ran memtest86 and it found no errors. My hard drive is almost new.

I'm using Xubuntu Lucid, and had to supply a barebones xorg.conf to get my monitor's native 1280x1024 resolution at 16bpp.  No Options are set; it just specifies the SiS driver, defaultdepth 16, and resolution 1280x1024. 

Should I just buy a real video card and disable the onboard SiS junk card? Has anyone got any ideas about what might work?

---

