---
title: "Cloning screen for presentations (projector)"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by sloggerkhan on 2007-03-25
I've browsed through the forums and all the multi-monitor guides I can find are for people who want separate desktops on their screens.

I'd like to make an xorg.conf for the open source ati driver that clones my laptop's lcd to the vga (and possibly dvi) out so that I can face my laptop to see what's being projected when I give a presentation that projects to my back.

Is there a simple way to do this?

(I'd like to do this under feisty, as I want to demo the next ubuntu release to an audience, but it's ok if the answer only works for edgy.)

---

### Post by srouquette on 2007-03-26
I made it work once, you can use the settings described [here](http://www.ubuntuforums.org/showthread.php?p=1773710).
MergedFB doesn't work on my computer (because my video projector doesn't send ddc information), but when I tweaked "MonitorLayout" to "CRT, LCD", the clone mode worked (probably because my video projector became my main screen)

---

