---
title: "Attn: ktemkin - Stuck Volume/Multimedia Keys"
date: 2009-04-25
forum: Hardware
---

### Post by dldeskins on 2009-04-25
Problems like in this thread:
[http://ubuntuforums.org/showthread.php?t=974723](http://ubuntuforums.org/showthread.php?t=974723)

I have a Toshiba Satellite U305-S7448 and upgraded to 9.04 last night.  I have the identical problem that I had with 8.10... that is, my volume control knob will "lock" the desktop and i can do very little else.  I cannot open menus nor type in the terminal.  I can hit the power button and restart, which is what I do.  If I don't touch the volume control knob, everything seems to work.

Thanks in advance
Don

---

### Post by dldeskins on 2009-04-26
bump

---

### Post by dldeskins on 2009-04-26
I checked the live cd and have the same problem.  Is there a way to disable the sound control knob or some other kind of work-around?

---

### Post by ktemkin on 2009-04-27
When I get a chance, I'll try and release a fix/patch/deb package, and something like Method #1 on my other post. 

In the meantime, you can disable your non-working keys in Keyboard Shortcuts, or try Method #2 on that post of mine.

If anyone can put me in contact with the evdev group, I'd really like to discuss the proper place to fix this bug.

---

### Post by dldeskins on 2009-04-27
> **ktemkin said:**
> When I get a chance, I'll try and release a fix/patch/deb package, and something like Method #1 on my other post. 

In the meantime, you can disable your non-working keys in Keyboard Shortcuts, or try Method #2 on that post of mine.

If anyone can put me in contact with the evdev group, I'd really like to discuss the proper place to fix this bug.

Good deal! and yes, I found out how to disable the knob looking through the other thread. 

Thanks

---

### Post by meditatingfrog on 2009-08-04
> **dldeskins said:**
> Good deal! and yes, I found out how to disable the knob looking through the other thread. 

Thanks

Dldeskins:

I have a Toshiba u305-s7448 (I pmed you awhile back to introduce myself).  Just wanted to let you know that method #2 worked for me to get the volume wheel to work, so if you get some time, you might want to try it (again if you already have).  The first time I attempted compiling, it didn't work, but I was able to get it to work by trying again recently.

Kevin

P.S.  As a side note, my laptop is running pretty well.  I have 9.04 also, and I just updated my Intel drivers.  I can enable desktop effects now, but when I do, the system is unstable.  I added the UXA to my xorg.conf file and so far it doesn't seem to be unstable (unless I enable desktop effects).

---

