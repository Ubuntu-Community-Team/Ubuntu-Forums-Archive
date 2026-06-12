---
title: "Dual Display on Dell D520 problem"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by aztektum on 2007-10-30
Everything on this laptop works great out of the box, but I hooked up an Acer AL1916W 19" widescreen to the dock and I can't set that screen as an extension of my desktop. All it does is mirror it.

The control in System >> Administration >> Screens and Graphics is greyed out to use it as a secondary screen (in fact what's weird is disabled is checked, but it is mirroring my display)

I'll post my xorg.conf if someone thinks the answer lies there, but if anyone has an idea off the top of their head....

Thanks!

---

### Post by aztektum on 2007-11-01
ok been dinkin' around with this, hosed my xorg file in so many ways, but i'm not dumb enough to forget a back up!

this is annoyin' though. i could really use the extra screen real estate.

---

### Post by aztektum on 2007-11-01
H'ok so:

the experimental Intel modesetting driver doesn't seem to like dual display much?

i deleted the entries in xorg.conf for the 2nd monitor (remember it was showing a mirror of the primary), second adapter, second screen and it's STILL showing a mirror.

the i810 driver doesn't let me do the 1400x1050 res on my laptop screen for some reason (even though that's the only entry i set in the xorg.conf)

glad composite desktop got included by default though!

---

### Post by timken240 on 2007-11-08
I have exactly the same problem..The second cloned screen is Grayed Out.
 And every attempt  of editing xorg.conf  only gives me "low graphics mode" after restart.
I will keep searching, if I find something i will post it here.
Cheers...

---

### Post by timken240 on 2007-11-08
By default Ubuntu 7.10 uses the Intel experimental driver in dell D520 laptops, changing this driver as aztektum suggested in this thread to the apparently more compatible i810  enabled the second screen or "dual monitor" in the "Screen and Graphics Preferences".
 I still can't figure out how to have the resolutions I want on both screens I am stuck with " 1024*768 " on the laptop and  even if it says I have " 1280*768 " on my external LCD (widescreen) I only have 800*600..

---

### Post by mobiusdim on 2007-12-17
the second part of this post is relevant..read it here

[http://ubuntuforums.org/showthread.php?t=641102&highlight=widescreen+intel](http://ubuntuforums.org/showthread.php?t=641102&highlight=widescreen+intel)

---

