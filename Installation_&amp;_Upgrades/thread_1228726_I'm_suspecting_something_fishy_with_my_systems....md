---
title: "I'm suspecting something fishy with my systems..."
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by Why-Fi on 2009-08-01
Yesterday I dual-booted new Ubuntu 9.04 with my old Vista. I did it according to instructions and apparently all went well. But the problem is, today, various things are happening. I suspect Vista is "fighting" against Ubuntu like it does everytime it finds something from third parties...

First, when booting onto Ubuntu, everything goes at it should and at max speed, it asks me for the internet password and then I do things normally UNTIL I open Mozzila Firefox. At which point it freezes and I have to reset my comp. I suspect it's the PCI wireless card's fault, as it is not well recognized by Linux (different brand appears in the connection menu) and it doesn't even log on to the networks it displays: it merely shows them. So I use a small USB internet pen I bought for my old Linux machine, and it works. But maybe what causes the freeze is having them "collide" at the same time. Tell me how to fix this please.

Then, when booting onto Vista, I found the boot speed is waaaay slower than it usally was, the RAM indicator fills to almost 100% at boot and things take lots of time to load, and it only stabilizes after a good while. I don't thing it's a virus, I've ran the anti-virus recently and it didn't find anything, and the only things I installed after that were Firefox plugins (and they were marked 5 stars and were recommended plugins) and Ubuntu. Could it be that Vista is "fighting" against Ubuntu upon finding it taking over the other partition? Please inform me.

Thanks in advance,
~Why-Fi

---

### Post by Sef on 2009-08-01
> Yesterday I dual-booted new Ubuntu 9.04 with my old Vista. I did it according to instructions and apparently all went well. 

What instructions did you follow?

---

### Post by ajgreeny on 2009-08-01
I really don't think the two OSs fight one another in any way.  I hope and presume you:-
a)  defragged a couple of times before shrinking vista, if you needed to shrink it, when installing ubuntu
b)  did not delete any files from the partition you now use for ubuntu when you installed the ubuntu OS, and that you 
c)  did not "move" the vista partition with gparted; shrinking it seems to be OK, but not moving it with gparted.

If you did all these things right, I suspect you have simply a need to run chkdisk or whatever it's called in vista, to make sure that the partition and file system is not faulty, and to repair any problems it may find.  I have never used vista, other than to shrink it with its own disk management tool, but as far as I'm aware, the vista install which is never used but still there, on my wifes laptop runs as well (badly?) as it did when the machine was delivered.  Check everything you can on vista itself to see if you can get things right.

---

### Post by Why-Fi on 2009-08-01
Well, Vista forced me to do a CHKDSK on boot just because I used Ubuntu to play a game that was on Vista's drive... And now works fine, although the slowdown immediately after boot still occurs (but no longer exists forever) and the internet issue on Ubuntu still exists (I can now use the internet without freezes but it will disconnect once in a while). At least both OS' are usable, even though the climax towards each other is of "DO NOT WANT"... :(

EDIT: An unrelated issue, but still an issue nontheless, why is YouTube different for me when using Ubuntu than it is on Windows? Is it normal or is it some bug?

---

### Post by ajgreeny on 2009-08-02
> EDIT: An unrelated issue, but still an issue nontheless, why is YouTube different for me when using Ubuntu than it is on Windows? Is it normal or is it some bug?Different in what way?

---

