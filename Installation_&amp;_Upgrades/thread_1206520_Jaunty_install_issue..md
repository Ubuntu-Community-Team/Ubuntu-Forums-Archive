---
title: "Jaunty install issue."
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by t0mppa on 2009-07-07
Ok, to get some background info, it isn't my first time installing Linux, already have half a dozen boxes with it.

[rant]And I had it running just fine on my laptop, until I took it to guarantee maintenance because of some WLAN issues, just to get those sorted while the guarantee is still available. And they for one reason or another decided to erase all my partitions and reinstall Vista on a single 320Gb partition.

Now, anyone who's played around with Windows knows that their built-in software usually is fairly crappy and Vista neatly writes some system files to the very end of its partition, so shrinking it becomes quite a problem. And I was lucky enough to get blessed with getting a rare "Access Denied" error with any free tools and didn't want to spend 50$ on commercial software that I need to run once. So, that was quite a frustrating project.

And last night when I finally got my Vista partition sized to 50 Gb, 50Gb of unallocated space left for Linux and the rest on a separate Data partition for both OS's fixed up, I thought I was finally done with the frustrating parts of the set up process, since Ubuntu's a lot easier to handle. Alas, that didn't really prove to be correct either.[/rant]

So, then I downloaded the Jaunty LiveCD and put it on my USB stick with UNetbootin. That didn't exactly work, since it tries to use a Xserver to show a neat GUI based install and the default ATI drivers don't work with my card, so only got to the Busybox.

Then I tried the alternative CD image instead, as that had proved useful in the past with other machines and it seems to work just great as in it boots off nicely and goes to the setup, get to choose language and set up my keyboard, but then it wants to proceed by installing the rest from the CD-drive. Naturally it fails to mount the CD, since all the data is on my USB stick and I can't tell it to just mount the USB drive instead.

So, what's up with that? That worked perfectly well with a USB stick on Hardy & Ibex. I suppose I could resort to burning CD's, but I think my CD burner is somewhat degraded, since last time I tried that I had to burn it 4-5 times, before it had no bad sectors (and yes, I tried slow speeds), so I'd rather not waste a bunch of CD's for that either.

Found a few notes on doing a network install from the Wiki, but they were all towards installing Ubuntu from another GNU/Linux environment and all the Windows alternatives include either other earlier version (XP/ME/NT) or the use of bootable floppy disks (no floppy drive on the laptop).

Guess I could resort to just installing Hardy and upgrading it, but that seems quite a troublesome way of doing things and figured I should ask if anyone around here has some simple tips or can just point me towards something I've overlooked.

---

