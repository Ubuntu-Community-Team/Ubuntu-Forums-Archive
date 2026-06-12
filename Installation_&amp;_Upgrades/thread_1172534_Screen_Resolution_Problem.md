---
title: "Screen Resolution Problem"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by fierojo on 2009-05-28
I just installed 8.10 on a desk top (mother board is Intel D945GCLF2), 30 gig SSD. Load was perfect. My Test display is a 15" Dell 4:3 LCD panel. After the install and restart, I started with the Ubuntu progress bar and then the display went to an "out of range message". I switched to a 16:9 higher resolution monitor and everything was fine. Reduced the resolution to 800 x 600 and switched back to the original monitor. Rebooted, and same out of range message. What am I doing wrong?
 
Thanks.
 
S. Joe Wynman

---

### Post by tommcd on 2009-05-28
What resolution are you trying to get? Since it is a 15" monitor I would guess that the optimum resolution would be 1024x768.

Try booting to recovery mode and choose the option "xfix fix video" then reboot back into Ubuntu and see if that fixes it.

If that does not work, try booting to a virtual terminal (without X) or to recovery mode, and use **xrandr** to fix the resolution. See this:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by fierojo on 2009-05-28
Thanks for the advise.  I was a Windows user, but am slowly converting over.  I have to learn all over again the things that were obvious to me before. How to I enter recovery mode during boot up?
 
Thanks.
 
S. Joe Wynman

---

### Post by fierojo on 2009-05-28
Just figured out how to get to the rerpair console.  It worked, thanks a lot!!!
 
S. Joe Wynman

---

