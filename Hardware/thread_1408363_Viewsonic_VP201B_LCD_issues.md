---
title: "Viewsonic VP201B LCD issues"
date: 2010-02-16
forum: Hardware
---

### Post by hotshot2000 on 2010-02-16
I recently installed Karmic on my dual-monitor setup, a Samsung Syncmaster 204b connected via VGA cable to a Radeon X800GTO and a Viewsonic VP201b connected via DVI-D to the same card.  I use the latter exclusively for watching DVDs (it's wall-mounted).  The Samsung works fine; however, the Viewsonic, after about 25 minutes of constantly being on, will begin to shimmer and develop vertical lines in a two or three inch block about an inch from the left side.  (The screen gets very warm to the touch as well.)  In addition, when booting the computer with just the Viewsonic plugged in, Karmic, which normally boots very quickly, stalls with a black screen after the "loading GRUB" message (instead of displaying the white logo) and will just sit there unless I cycle power to the monitor, after which it will finally finish booting.

I tried a trick I saw on another thread to do "sudo dpkg-configure xserver-xorg" but it has not helped.  It seems to me what's happening is that Karmic is overdriving the monitor, causing it to overheat.  This didn't happen in Windows (which I no longer have installed on that computer) and at least worked at some earlier point in Ubuntu (I can't remember if it was before or after I installed Karmic; I used to use Jaunty but did a clean reinstall for Karmic), because I watched a two-hour movie at some point with no shimmering or lines appearing.  Now, however, I can't watch anything for more than about 22-25 minutes without the screen shimmering.  I would have thought this a hardware problem except that it worked in Windows and at some earlier point in Ubuntu; either Karmic or some recent kernel upgrade has caused it to stop working.

Any ideas?  Thanks in advance!

---

