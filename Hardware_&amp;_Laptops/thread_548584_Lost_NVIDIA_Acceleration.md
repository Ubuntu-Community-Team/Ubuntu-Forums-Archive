---
title: "Lost NVIDIA Acceleration"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by Stealth on 2007-09-11
After a recent kernel update my compiz is running like molasses! I see the CPU being eaten alive and I have to do a "metacity --replace" to fix it. The kernel is 2.6.20-16.31 and I have a feeling the problem is that the restricted modules is stuck at 2.6.20-16.29. However, I got the 386 kernel and have the same issue, and I've used the envy script to uninstall and reinstall the drivers on BOTH versions and it still won't work! Weird thing is that X isn't crashing, it's running of "nvidia" in the Xorg.conf file, it just won't accelerate 3D stuff. What can I do?

---

### Post by JC Casiano on 2007-09-11
Have you looked in /etc/X11 to see if you have any previous copies of xorg.conf?  If you have a previous copy, rename the current copy and make an older copy active, then restart X from the login menu.  

I have played with Envy, and while I found it interesting I ended up reinstalling the NVidia drivers via Adept, fixed the LCD option anomaly, and then manually reconfigured xorg.conf based on a prevsious configuration.  I've found that with my notebook it's quite possible to put too many NVidia options in xorg.conf, and that resulted in "choppy" graphics and general mayhem with Beryl.  It might be possible that Envy inserted a number of options that either don't apply or don't work correctly in combination with other options for your adapter, and you may have to selectively disable some.  

Oh, just an FYI, I'm on Feisty, with an NVidia 420 Go (32MB).  I was on Edgy, couldn't get Beryl to run correctly, so I upgraded my machine to Feisty, spent a lot of time debugging, finally got Beryl to run smoothly.  Based on what I learned in Feisty I could probably go back to Edgy and make Beryl work, but then I'm liking the changes in Feisty a lot, especially in the wireless configuration.

I'm not on my home machine so I can't be specific, but if you don't have any success I can post some suggestions later.

---

### Post by Stealth on 2007-09-11
Yea, but a kernel update like that doesn't even mess with the xorg.conf does it? It's been the same, and it was only afterwards that the acceleration was killed. I'll probably end up checking all of that though.

I was also thinking about just jumping on the Gutsy boat, as I normally start using the versions once they hit that 5th release (Flight 5, or in this case, Tribe) but oddly enough I can't use that update-manager -d command since it says it can't find my dist or something. :P I also seem to recall reading issues with NVIDIA and X.org 7.3 or something, so that might not be the best solution right now either. :(

---

