---
title: "Third WXGA Post in as Many Days."
date: 2005-11-21
forum: General Help
---

### Post by fontosaurus on 2005-11-21
Okay, I feel like I'm getting a bit closer to getting this resolved, but I'm not quite there yet.  Here's the deal...I bought a new Dell XPS M140 laptop, specifically to run Ubuntu on.  The native screen resolution is 1280x800, yet I cannot get the system to run in anything but 1024x768 (or 800x600 and 640x480, but what's the point?)  Anyway, here's my salient system specs:

Bios: A02 (11/06/2005)
Graphics:  Intel Media Accelerator 900 (915 chipset), WXGA 1280x800 screen

Initially, I followed Shakin's post, here:
[http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)

But came to the conclusion that the 810 set and the 915 set might not jive, so I did the following:

- run 'wget http://ftp.psn.ru/debian/pool/main/9/915resolution/915resolution_0.4.7-1_i386.deb'
- run 'dpkg -i 915resolution_0.4.7-1_i386.deb'

- run 'sudo /usr/sbin/911resolution -l'

This is where things start going downhill.  Of the reported resolutions, none matched my desired settings.  

Now, in that same post, jr_G-man reports that changing his BIOS version from A06 to A09 seemed to resolve his issues.

Anyone have any ideas as to whether or not that will work here, and how I would go about it, if so?

---

### Post by jr_G-man on 2006-03-10
Well, I guess we've come full circle.  I just ordered an XPS M140...so, I'll be looking into all this myself.  We'll see what we can come up with.  :)

---

