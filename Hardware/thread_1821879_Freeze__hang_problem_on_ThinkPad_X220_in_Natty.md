---
title: "Freeze / hang problem on ThinkPad X220 in Natty"
date: 2011-08-09
forum: Hardware
---

### Post by maysamemadi on 2011-08-09
I recently purchased a Lenovo ThinkPad X220 and installed Ubuntu 11.04 64-bit on it. Got everything to work fine except that every few hours the system freezes, everything hangs and stops working. Then I'll have to force shut down the system by pressing and holding down the power button and restart, losing all the unsaved work every time. It happens so randomly and frequently, with no prior warning, that I haven't been able to figure out what causes it.

I searched around a lot for a solution to this bug and the only suggestion that I found was to upgrade the kernel to 2.6.39+. I installed the vanilla kernel version 2.6.39.4 but the problem still persists. Is there any other solution?

Thanks for your help :)

PS: This is my first post here. Hope I've posted in the right subforum.

---

### Post by tfnico on 2011-08-13
I've got the same problem. I just installed Natty 64 bit on a Thinkpad X121e a few days ago, and every few hours it completely freezes (no mouse moving, no keyboard).

I found a good start is to read [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

As the tip given in the article above, the next time it happens I'll try ssh'ing into the laptop, and see if there's any response (you have to install ssh-server up front in order to do this).

I've seen a lot of 'wireless drivers' mentioned in forums when googling, but this is a shot in the dark. I reckon it's pointless to try any random fixes before I narrowed down the problem a bit more.

In the end, if nothing works, I'll try installing a 32-bit Ubuntu instead, I reckon. I need a laptop I can do presentations on, and this won't do.

---

### Post by tfnico on 2011-08-13
Tiny update: I've now gone over 5 hours without a freeze, doing pretty much the same stuff as I was doing before (fiddling with terminals, various programs and doing Java development).

The only thing I did change before this was doing this:

[http://superuser.com/questions/282746/natty-freezes-constantly-after-install/282748#282748](http://superuser.com/questions/282746/natty-freezes-constantly-after-install/282748#282748)

The symptoms were different (the poster could still use his keyboard), but maybe I still got lucky with this fix. Will post back later if it freezes again.

---

### Post by dRbiG on 2011-09-17
I've also had two random freezes recently.
Physically nothing's responsive, but I haven't tried ssh - hopefully I won't have a chance as I did turn off the 'sync to vblank' as of previous post.
I remember reading somewhere that the vblank syncing may results in some stuff that never gets a chance to do so and, well, freezes. So the whole solution does sound plausible.

Time will tell...

---

### Post by fictivetoast on 2011-11-11
I've been having this problem on my x220 with both 11.04, and now 11.10, on both Unity and Gnome Shell.  Did anyone ever pin down what's going on ?

---

### Post by tfnico on 2011-11-12
Nope, I haven't had any problems since. Also upgraded to 11.10 recently, and no freezes.

---

