---
title: "DVD playback on old laptop"
date: 2009-12-09
forum: Hardware
---

### Post by benoitvm on 2009-12-09
Hello

I hoped to recycle an old DELL Inspiron 4000 (700 MHz PIII & ATI Rage Mobility M3) for simple tasks by installing Ubuntu.
I found elsewhere in this forum the settings to get the full resolution for this video adapter, unfortunately, while basic office & Internet tasks are ok, I am disappointed by the performance in DVD playback: under Windows XP or earlier versions, the CPU of this unit could easily cope with DVD decoding and related video smoothing, while under Ubuntu 9.10, with VLC the CPU is at 100% and frames are dropped, I am not even thinking about deblocking, smoothing etc.
Is there any hope to get this nearly 9 years old robust machine do something better with DVD playback (rather than reinstalling Windows XP :oops:) ?

PS: I am far from being an Ubuntu expert, I'm just discovering it...

---

### Post by HappyFeet on 2009-12-09
XP is able to handle DVD because it uses less resources than a modern OS like ubuntu. Remember, XP is almost 9 yrs old at this point, and any old OS is going to use less system resources. I'm afraid your lappie just does not have the horsepower to handle ubuntu *and* DVD playback.

You could try a lighter linux distro such as Puppy linux and see how it handles it.

---

### Post by benoitvm on 2010-01-11
Not sure I agree...
Even if my laptop is somewhat outdated....when Ubuntu is *idle*, it does not have to "use more resources", most of the CPU cycles are available for DVD decoding (same for Windows XP); the fact that Ubuntu is more recent than XP does not change this fact.
So I guess that it's a matter of the capability of the graphics card driver, which benefits from some form of acceleration under XP, and is probably more basic under Ubuntu (b/c noone bothers writing an advanced Ubuntu driver for such an old GPU ?), and hence, puts the full load of mpeg2 decoding on the user-mode application (VLC e.g.).
No ?

---

