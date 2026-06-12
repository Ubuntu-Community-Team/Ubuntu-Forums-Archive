---
title: "HP tm2 Black/Blank screen on start up"
date: 2011-01-06
forum: Hardware
---

### Post by downthesun01 on 2011-01-06
I've been trying to install Ubuntu 10.10 on this netbook/tablet for a while now. The issue that I keep running into is the following:

The install goes well am I'm able to update everything and restart the system with no problems. A day or so later, when I try to start up my pc, I get a black/blank screen where the "Ubuntu" screen usually appears. The same thing happens no matter how many times I restart my computer. I believe the problem is related to my pc's dual video cards (battery power- Intel, AC-Radeon)

To fix this I've tried:

Temporarily editing Grub parameters to xforcevesa.(No change)

Temporarily editing Grub parameters to nomodeset. (Gave me a terminal-looking screen. Couldn't do anything with graphics)

Opening and closing the lid to my laptop several. This was recommended in a post somewhere while I was looking online for a solution. (No change)

Trying to brighten the screen with F3 (No change)

Does anyone have any suggestions that I should try?

---

### Post by avion2007 on 2011-01-06
Does this netbook have an external vga connector? Have you tried that?

My HP62 did this on the install only, however connecting to a crt monitor I was able to see what was  happening and read the error msg's.

---

### Post by Favux on 2011-01-06
Hi downthesun01,

Apparently you're right and support for dual cards is the problem.  They've been shutting off the ATI card to get things to work.  It also prolongs battery life.

See:  [http://ubuntuforums.org/showthread.php?t=1616327](http://ubuntuforums.org/showthread.php?t=1616327)  for the simplest method.  I'm not so sure about some of the other suggestions.

or:  [http://ubuntuforums.org/showpost.php?p=7933876&postcount=11](http://ubuntuforums.org/showpost.php?p=7933876&postcount=11)
from:  [http://ubuntuforums.org/showthread.php?t=1410752](http://ubuntuforums.org/showthread.php?t=1410752)  This thread is a good source of general troubleshooting.

For automatic rotation I suggest the Magick Rotation applet:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

Hopefully the dual card problem will be corrected shortly, if it hasn't been already.

---

### Post by downthesun01 on 2011-01-07
Thanks Favux. The link you posted seem to have fixed the problem, at least for now. Much appreciated.

---

### Post by LiquidSolstice on 2011-06-13
Guys, I don't mean to resurrect a dead thread, but I've figured something out. I posted this on the Tm2 workarounds thread as well.

It's not that the screen won't turn on, it's that the backlight is off, and is unable to brighten back up again. Don't believe me? Look very, very closely at your "blank screen". You can just barely make out that the screen is still indeed on.

Try it yourself. When logged in (after doing the close lid/open trick), open up some video or some activity that has a lot of movement and screen changes in it. Then, use the F2 key, and drop your brightness all the way until the screen is off. You can still see the movement/video on the screen if you look very hard. However, once it is, you'll find that pressing F3 doesn't bring it back. This is what we need to fix.

Is there a way to completely remove the lowest brightness setting in some sort of configuration file? I'm 99% sure that this will fix the issue.

---

