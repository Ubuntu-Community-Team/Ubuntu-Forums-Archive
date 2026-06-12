---
title: "How to I get to the eee PC 900A's bios or boot screen?"
date: 2008-11-06
forum: Hardware
---

### Post by wendallsan on 2008-11-06
Hi Everyone, I just bought an eee PC 900A and want to throw ubuntu-eee on it.  I can't for the life of me get to my bios or boot screen.  I've read in the documentation and online to press either esc, f2 or f11 to get to these screens, but I'm not getting anywhere with any of them. When I get to the Asus 'starting up system' screen and press these keys, I get symbols on the screen such as [^ for escape (and other [... codes for F2 and f11), but it still goes straight into Xandros, the only difference being that the touchpad doesn't work and I have to use keyboard shortcuts to reboot the machine.  I've tried pressing these keys once, many times, press-and-hold, started pressing them before hitting the power button, after, etc etc.  What am I missing here? BIOS is nothing new to me, but man it's lame that I can't even get into it!  Any help is greatly appreciated.

---

### Post by lhong1987 on 2008-11-07
It seems that when you "shut down" xandros, it doesn't actually shutdown.
for faster reboot xandros might actually hibernate rather than shutdown (haven't actually checked if that was the case though.)
anyhow, here's how i did it.

take out the battery pack
unplug the 900a while that starting up system screen comes up
plug it in again and power and wait for the bios prompt.

---

### Post by drcrash on 2009-07-07
You shouldn't need to take the battery out.

Start tapping F2 as soon as you hit the power, and that should throw you into the BIOS setup.

You need to TURN OFF QUICKBOOT.  That's NOT the same thing as BOOT BOOST, so make sure you go into the boot options submenu.

I also put the external device (?) option first in the boot order... ahead of the internal SSD anyhow.

When installing, if you first do the "check disk integrity" option, you will probably get 1 error found.  That's a known minor bug.

The problem is a file in the main/p/ppp subdirectory that has the wrong name.

If you go ahead and install it will work, but you can't install ppp from the image.  You can install it from a repository and all should be well.

[https://bugs.launchpad.net/ubuntu/+source/mobile-meta/+bug/360925](https://bugs.launchpad.net/ubuntu/+source/mobile-meta/+bug/360925)

---

