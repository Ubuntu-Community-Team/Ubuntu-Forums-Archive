---
title: "AOC 2219S-1 LCD Widescreen Monitor plus NVIDIA GeForce 9400 GT configuration"
date: 2009-06-10
forum: Hardware
---

### Post by jefkin on 2009-06-10
Hi gurus.

I got this huge beautiful AOC widescreen LCD last year in October.  Plugged it into my then computer and threw a major fit trying to get anything better than the default generic 1280x1024.

The monitor plugs-n-plays with windows (gasp) up to 1680x1050.

But since I work for a living I couldn't spend any more time fighting it.  I lived with 1280x1024... that is until the motherboard on my computer got fried.

I bought a better computer, and much better video card NVIDIA GeForce 9400 GT.  Which seemed to work great out of the box.  That was until I found out that I wasn't actually using any of my video card power because it was just treating it as a generic vesa.

So I found some instructions here on ubuntuforums to install the NVIDIA display drivers.  I tried to follow them, only to be rewarded by a black screen reboot and the low quality Xwindows warning.

Well, I thought I just pop my old xorg.conf back to get back where I was and found that something had destroyed Ubuntu's (or probably X11's) idea of my monitor, and so every reboot since, I'm stuck with 800x600 not even the 1280x1024 that I had settled for before.

A whole day messing around with this and I'm no closer than when I first tried this. :(  

I'm using 8.04

Question A) Is there a definitive NVIDIA driver installation process?

Question B) Is there a driver? or xorg.conf setup for my monitor so I might enjoy the full capacities?

Question C) Is there a way to get these two to play together?

... Should I upgrade?  Some of the posts seem to suggest that 8.10 or 9.x are better at the whole NVIDIA thing.

---

### Post by jefkin on 2009-06-11
Well the good news is I found a solution, upgrading from 8.04 to 8.10 solved all my problems.  I highly recommend it if you're having trouble with your nvidia card.

---

### Post by jefkin on 2009-07-02
Turns out I was a bit premature with my praise of 8.10 regards the NVIDIA drivers for me.  It wasn't until I got to 9.04 that the drivers from the installed packages worked/recognized my card.  

So, I amend my above praise to be 9.04 for some NVIDIA cards.

---

### Post by CMOS4081 on 2009-07-02
Hi there,
Install the restrictive Nvidia drivers.
Then from a terminal type "sudo nvidia-settings" with no quotes, put your root password and then play with the Nvidia control panel. Enable the second display, change the resolutions if you wish, etc etc etc...
Works like a charm for me.
Good Luck

---

