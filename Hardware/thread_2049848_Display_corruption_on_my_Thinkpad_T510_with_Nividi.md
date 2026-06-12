---
title: "Display corruption on my Thinkpad T510 with Nividia drivers on 12.04"
date: 2012-08-29
forum: Hardware
---

### Post by samtregar on 2012-08-29
Hello all. Ever since I upgraded from 11.10 to 12.04 I've been having display problems. Basic symptom is that the display buffer appears corrupted. It seems to affect the alt-tab display most often - instead of seeing little pictures of the windows the boxes for the windows have garbage in them, random text and messed up images. After that it spreads to the status bar at the top of the screen and then into windows themselves - for example, Emacs will have garbage text across the top of the window and inside the buffer area. Sometimes switching to a VT and back to X will clear it, sometimes not. Eventually the system will lock up and I'll have to restart.

So far the only fix I've found is running Unity 2d, but frankly that's not great at all. It definitely feels like second-class environment.

I've tried upgrading my Nvidia drivers twice - first to 304.37 then to 304.43 yesterday, both times using Nvidia's installer. Before that I was running 295.59. I'm fully updated running the 3.2.0-29-generic kernel. This machine is a Thinkpad T510 with a dedicated GPU - the NVS 3100M, aka the GT218.

I don't see anything useful in my X logs or in syslog, but let me know if you want to see them anyway.

Thanks for the help!

Sam

---

