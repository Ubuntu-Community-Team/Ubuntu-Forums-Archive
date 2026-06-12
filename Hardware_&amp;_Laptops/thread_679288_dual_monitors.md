---
title: "dual monitors"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by VinceW on 2008-01-26
I just installed Ubuntu 7.10 on my Sony Vaio PCG-K47.
So far all is good except I can not get my dual monitor setup to work.
Second monitor is a Sony SDM-HS75P which is listed in the monitor selection.
Any suggestions welcomed.
Thanks,
VinceW

---

### Post by derrick81787 on 2008-01-28
The GUI for setting up your monitors seems to be broken in Ubuntu 7.10  It still isn't very hard to set them up, though.  I've posted instructions about how to do this on my site [http://ubuntuisms.com/main/?p=38](http://ubuntuisms.com/main/?p=38) .  I would post them here, but it just saves me a lot of typing this way (and a lot smaller of a chance of typos too).  Let me know if this helps you at all.

- Derrick

---

### Post by mocoloco on 2008-01-28
I second that broken GUI setup comment, there were promises of never having to edit xorg.conf but alas it didn't quite get there in Gutsy.  Hopefully Hardy will take care of it.
I found though that using the GUI did get things started, in my case it set up xinerama and both monitors, but the resolutions were messed up and both screens would not show the whole display and would require scrolling at the edges.  I fixed it by removing the resolutions that I didn't want in xorg.conf.

Not to hijack the thread but I think this is still on topic, why derrick did you go with xrand over Xinerama, and is one better than the other for certain situations/hardware etc?
I ended up writing a script that would swap out my actual xorg.conf file for dual or single monitors, a bit more cumbersome maybe than your solution.

---

### Post by sammydadams on 2008-01-28
you might be able to use something similar to the xorg.conf in my post....not sure if it'll work but i use it to hook up on s-video, but you should be able to run nvidia-settings in terminal while it is hooked up....i haven't seen what they are saying is broken....you can also find xorg.conf settings in the forums that you can follow...just back up your original.

---

### Post by derrick81787 on 2008-01-28
> **mocoloco said:**
> Not to hijack the thread but I think this is still on topic, why derrick did you go with xrand over Xinerama, and is one better than the other for certain situations/hardware etc?
I ended up writing a script that would swap out my actual xorg.conf file for dual or single monitors, a bit more cumbersome maybe than your solution.

xRandR will switch between monitors on the fly with no need to restart X.  That way you don't have to close out your applications when plugging into an external monitor.

I actually did use Xinerama in Feisty, but xRandR wasn't as good then.  They've made a lot of improvements for Gutsy, and so I went with it this time around. I'm not sure, but I think that is what displayconfig-gtk is supposed to use as it's backend.  Don't quote me on that, though.

- Derrick

---

