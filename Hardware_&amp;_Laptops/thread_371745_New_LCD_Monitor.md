---
title: "New LCD Monitor"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by jpl80 on 2007-02-27
I'm currently using Ubuntu 6.10 and a DELL CRT monitor. I want to switch to a 19" LCD so that I can get a higher resolution and have more space. My question is how do I switch? Should I just shutdown, plug in the new monitor and then boot? Will it automatically detect my hardware or will I have to run something?

I use the standard integrated VGA output that came with my Dell GX150. The monitor I want to get is a Samsung 941BW Widescreen 19" Analog/Digital LCD display

The essence of my post is, **what should I be prepared for when I plug in the new monitor...**

Thanks,

---

### Post by Qrk on 2007-02-27
I haven't had to change monitors between brands before, so it might not be quite so easy for you. Still, you shouldn't have a problem.

Turn off your computer and plug in your new monitor. Most likely X won't be properly configured, so you'll have to run the command 

```
sudo dpkg-reconfigure xserver-xorg
``` 

and choose the settings for your new monitor (note, your video card settings should stay the same). If, by some bit of misfortune, the graphical interface doesn't start, you can still run the above via the command line.

---

