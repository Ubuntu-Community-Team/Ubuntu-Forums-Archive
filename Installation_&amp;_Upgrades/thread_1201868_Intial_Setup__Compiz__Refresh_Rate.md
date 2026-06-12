---
title: "Intial Setup / Compiz / Refresh Rate"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by Shibblet on 2009-07-01
Upon initial setup, I found that Compiz-Fusion detects my displays as 50hz.  

This might be a standard thing in Europe / Asia, but in America / Japan, our displays are standardly set at 60hz.

Everything looks a lot better after I ran Compiz-Config Settings Manager, entered General Options, clicked on the Display Settings tab, then turned off the display auto-detect, set it to 60hz, and turned on Sync to Vblank. (optional, but it seems to eliminate tearing).

So hopefully this helps a lot of people...

But my questions are...  Why didn't Compiz detect the screen correctly?  Is it defaulted to 50hz?  Couldn't it be autodetected correctly upon setup?

---

### Post by ibuclaw on 2009-07-01
Your issue wouldn't be compiz's fault.

Probably a mixture between bad detection from Xorg and settings applied by Gnome.

Although, the fact that you can set the refresh rate to 60Hz is a sign that there is nothing wrong here, just a bad guesstimated auto default.

Regards
Iain

---

### Post by Shibblet on 2009-07-01
This is complicated.  I looked at the xorg.conf, and it's entirely "Default Device" in ever facet.

So the default is 50hz, how do I change it to 60hz?  Without having to play edit xorg.conf. It's too confusing.

---

