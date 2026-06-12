---
title: "Living with a small screen"
date: 2008-11-23
forum: General Help
---

### Post by unkilbeeg on 2008-11-23
I have an old (very old) LCD monitor whose native resolution is 800x600.  It's a 15" monitor, perfect for the spot it's in.

The problem is that a fair amount of software in Hardy assumes a much larger screen, and quite a few dialog boxes have important controls that are inaccessible because they're off the screen.

Now it seems to me that some time back when I was running Gentoo on this box, I had a lot more room on the desktop.  I was running a pretty old version of Gnome, though, so it may have had a more compact layout at that time.  I've changed my font DPI to 72 from 96, and I get a drop in quality, but a little more room.  That helps some.

However, it seems that in the past I've been able to set my desktop to a larger size than my resolution and then just scrolled around the desktop.  I don't particularly care for that style of operating, but given my constraints, I could live with it. 

Is this still possible (or am I dreaming that it ever was?)  Does someone know how I can set this up?

---

### Post by tgalati4 on 2008-11-23
Try XFCE.

Try a live CD of Linux Mint Darnya XFCE.

---

### Post by unkilbeeg on 2008-12-24
Good call.  I didn't use XFCE, but I booted into MINT 4 and the resolution worked correctly -- the monitor supports 1024x768.  Copied MINT's xorg.conf over the top of the one from Ubuntu, and all was well.

MINT 6, incidentally, was no help.  It has the same broken detection of video resolution that current versions of Ubuntu do.  They work fine on new hardware (like my work machines) but not so well on older stuff.

---

