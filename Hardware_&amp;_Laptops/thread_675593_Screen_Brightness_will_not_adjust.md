---
title: "Screen Brightness will not adjust"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by KingArthur10 on 2008-01-22
Well, I've looked around the forums for about a half an hour and haven't found anything that solves my problem.  Well, I have a gateway C-140XL with an ATI 2300HD.  My brightness controls don't seem to work at all except for one situation.  If I press Fn + F8 twice, it dims the screen to the dimmest setting, and then one more press of that combo brightens it back to 100%.  I have tried the Fn + up/down and that brings up the little sun symbol in the center of the screen, and the slider works, but it doesn't actually dim the screen.  I can go into power management and manually adjust the sliders and again, it doesn't dim the screen.  Actually, in the power management control panel, even if I move the slider to 0% it doesn't dim it at all.  I'm not sure what I need to do to solve this problem.  If someone is willing to work with me to troubleshoot the problem, it would be greatly appreciated.

---

### Post by KingArthur10 on 2008-01-24
Bumping for all those other c140 owners out there.  It's becomming a popular tablet, and I hope we can get this fixed somehow.

(FYI, everything I've been learning how to tweak and fix with this laptop I've been consolidating on [tabletpcreview forums]("http://forum.tabletpcreview.com/showthread.php?t=8603&page=5"), so your help won't go to waste).

---

### Post by KingArthur10 on 2008-02-17
Well, I've found a rudimentary fix for certain occasions.  First off, this is actually a graphics driver issue, not actually an Ubuntu issue.  The fglrx drivers only allow this laptop to switch between full and minimum brightness.  I might report a bug on that to AMD's support site.  So, if you are using the fglrx driver, you're SOL and only get two brightness levels.

Now, if you have the radeonhd drivers installed, there is hope, but it's not very elegant,  The drivers themselves don't have certain bios features enabled to make writing the driver easier and more stable.  This includes the screen brightness adjustments.  Instead, the radeonhd drivers will just accept and maintain whatever brightness the terminal sent on to them when X boots or is switched to.

Now for the radeonhd fix: ctl+alt+f8 should switch you to a terminal.  From there, you will want to adjust your brightness using the Fn key combos (fn+up, fn+down, or fn+f8).  Then type ctl+alt+f7 to switch back into the X server.  There you go.  Now you're in business and able to adjust your screen brightness whenever you want.

I hope this helps anyone who needs it.

---

### Post by rdc.lingua on 2008-03-24
I'm on a Gateway 6960 with the Intel 915 gfx set.  I'm having the same problem with the brightness settings.  At least now I know *why* this is happening even if I can't fix it.  Thanks for the info!

---

