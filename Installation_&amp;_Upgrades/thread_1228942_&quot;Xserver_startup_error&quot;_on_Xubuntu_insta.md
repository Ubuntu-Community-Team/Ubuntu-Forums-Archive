---
title: "&quot;Xserver startup error&quot; on Xubuntu install"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by Velvet_Man on 2009-08-01
Hi,

I'm trying to install Xubuntu 9.04 on an old HP Pavillion 8565C. It's got a Pentium 3 500Mhz CPU and 384MB RAM.

It's running Windows 98 just fine right now, but it's got a ton of crap on it that's slowing it down, so I thought I'd format and start fresh with Xubuntu.

The install CD comes up fine, the memory test returns no errors, but when I go to install it, I get an xserver startup error and then it goes to the Ubuntu terminal prompt.

Just for the heck of it, I tried throwing an old 32MB TNT2 video card in there (instead of the onboard video), but that didn't change anything.

Any thoughts?

---

### Post by running_rabbit07 on 2009-08-01
I see that you have done the memtest, have you tested the install disk?

---

### Post by Velvet_Man on 2009-08-04
Hi,

So the disk was fine, too. 

I eventually came to some sort of solution, however.

I noticed that when it was in text mode a ton of error messages were going up the screen. I caught a few of them. I'm a bit new to Linux, so I'm not sure what most of it's about, but one that caught my attention said something to the effect that the bios date (1999) was past the cutoff date (2000).

So on a whim I decided to try to install 8.04 instead of 9.04 and everything installed fine and it's working perfectly.

The only problem now is when I go to the HP page, their instructions for updating the bios to its 2000 version (last update available), it's all for Windows98. 

Does that mean I'm stuck at 8.04 until I find a way to update the bios?

---

