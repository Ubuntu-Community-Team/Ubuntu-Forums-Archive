---
title: "Blank screen during POST / boot"
date: 2005-07-31
forum: Hardware &amp; Laptops
---

### Post by wunch on 2005-07-31
I just installed Ubuntu and the nvidia driver (which I think is to blame) and now, every time I boot up my LCD monitor is blank (getting no signal) during POST or any console-like activity (like showing the verbose output of devices and processes loading/stopping during startup/shutdown).  I can't see the grub menu, either.

I know everything is actually working because I can see the HDD LED lighting, and once it gets to the point that a graphical screen is showing (with the nvidia logo), I can finally see it.  When it gets to this point, everything is fine.

The same is true when I try to boot into windows xp (which I can access by remembering that it's the bottom menu entry in grub and just hitting the down arrow key a bunch of times then hitting enter; the screen is still blank at this point).  I don't see the windows logo or boot screen either.  The monitor is blank until the gui logon screen pops up, after which I can finally see it and everything works fine.

My computer is not a laptop or anything proprietary like that.   It's a homebuilt with an Asus A8N-SLI Deluxe motherboard and a PCI-X GeForce 660GT.

I strongly suspect that the nvidia linux driver install did something strange to my video card.  I was not having this problem, either in Ubuntu or WinXP, until I installed that driver.  Also, I don't think changing any config files will correct the problem, as it happens even before linux boots.  I have no idea how to fix it, and any ideas would greatly be appreciated.

---

### Post by seatek on 2005-09-20
I just experienced a very similar problem and have posted my description here:

[http://ubuntuforums.org/showthread.php?t=67605](http://ubuntuforums.org/showthread.php?t=67605)

---

