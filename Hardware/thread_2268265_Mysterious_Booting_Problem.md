---
title: "Mysterious Booting Problem"
date: 2015-03-07
forum: Hardware
---

### Post by 56es8lTI on 2015-03-07
Yes, this really is a *hardware* problem!

I have an older machine I have been using for a Lubuntu platform.  It's always been rock-solid.  This past week or two, I've been doing a clean-out and reorganization of my office, moving the computers around, etc., etc.

After getting everything back in place, I powered up and it appears that Lubuntu had a catastrophic filesystem failure.  During the re-install, I also had problems.  Then I noticed that the system apparently wouldn't even try to reboot when I hit reset.  It showed *no screen activity* at all.  The system's lights came on, but nothing on-screen until I powered down at the switch and started over.  At that point, it would eventually go to CD to boot the live Lubuntu OS.  RAM tests good, the HD tests good.  This morning, when it was cold, it took about twenty attempts to get rolling (I'm using it in "Live" mode now).

It seems to me that I've bumped something loose moving this beast around.  Could a loose video card, say, cause these problems?

Any other thoughts on this?  What should I be looking at when I drag this thing out and look at its guts?

Thanks for any inspiration!

---

### Post by weatherman2 on 2015-03-07
If you have more than one computer, try swapping power supplies in this one that won't boot reliably.

---

### Post by 56es8lTI on 2015-03-07
Well, incredibly, it looks like there were two problems:

1:  There was a blown video card (popped capacitors were a dead giveaway) that was accounting for the absence of screen activity.  I drug out some antedeluvian SiS PCI video card out of the junkpile and I'm back in business.  Now, I just have to scrounge a less-obsolete AGP card somewhere.

2:  The filesystem problem was just this stupid, "errors were found while checking the disk drive for /" bug. :mad: Not entirely clear on how to fix that mess.

And a bonus third:  During updates, it errored out saying there was a **programming** bug in Synaptic.  Huh?

---

### Post by 56es8lTI on 2015-03-07
OK, so here's the latest:

I chucked the old SiS PCI vid card and plugged into the board's native video -- which is supported on Lubuntu.  Works OK.

I found a fsck fix for that file system problem, though I don't fully understand it nor why it works.  It does, so I suppose I should just let it go.

Tried updating again and didn't get the same error, though one program didn't update (not unusual).

I guess this is about as good as it gets. :)

---

