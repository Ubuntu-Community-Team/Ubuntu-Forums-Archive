---
title: "Adding a 3rd monitor"
date: 2010-03-18
forum: Hardware
---

### Post by mrjawbones on 2010-03-18
I have a laptop running karmic and have a dual head setup at the moment using the laptop screen plus an external monitor connected to the dock.  I need to add a 3rd monitor, so I was thinking something along the lines of an external video adapter like USB-to-VGA (or DVI).  Does anyone know of one that is supported because the two I've tried so far I can't get Linux drivers for.  

Thanks in advance...

---

### Post by jrssystemsnet on 2010-03-18
DISCLAIMER: I have not done this personally.

However, the [Kensington multi-display-adapter](http://www.us.kensington.com/html/17534.html) family should be a working example of hardware driven with the sisusbvga driver.  See [this old thread](http://ubuntuforums.org/showthread.php?t=260863) for a rather old example of getting it up and running.

If you go this route, don't leap right into repeating everything you find in that thread I linked - it's pretty old, and for all I know the adapter will "just work" right out-of-the-box if you plug it into a Karmic install.

One thing I can warn you of, from experience - Desktop Effects (ie, compiz) and multi-head are very likely not to want to live together on the same system.  So if you go this route and you're having trouble, you might want to try disabling compiz before tearing your hair out completely.

---

### Post by mrjawbones on 2010-03-19
Thanks for the lead, I'm going to check it out....

---

