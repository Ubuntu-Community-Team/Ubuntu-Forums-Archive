---
title: "Dual Boot Problems on an Asus G50V laptop"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by HH60Gunner on 2009-03-29
Ok, so I convinced a friend to use linux and he was well impressed with my laptop running kubuntu.  However we ran into so many problems with his laptop.  The first was installation, we couldn't get any linux disc to finish installing.  Eventually I found out that it would work if I went into the bios and changed the hard drive mode from enhanced to compatible.  After doing so the install went smooth.  Took some real work to get his wifi card to actually see access points but after some time that was working too.  Now the problem is that, if he tries to log into windows it gets the bluescreen during boot up.  My guess is that it's because the vista partition was made with the hd in enhanced mode.  However if I change it back to enhanced I don't get a boot up screen.  How can we go about making both of these systems work right?

---

### Post by Mark Phelps on 2009-03-30
How did you create empty space on the drive for Ubuntu?  Did you use the Ubuntu installer to shrink the Vista partition? Or did you use the Vista Disk Management function to do that?

If you did the first, it's possible you corrupted the Vista OS partition.  The only fix for that is to boot from your Vista DVD and run Startup Repair.

You DO have a Vista DVD, right?

If you don't, you can torrent a Vista recovery CD from the Neosmart forums website.

---

### Post by HH60Gunner on 2009-06-26
this is an older thread but I thought I'd post up the fix action.  It turns out the bios was set to enchanced mode for the HD.  So I switched it to compatible than reloaded windows and linux and it worked like a charm.  Turns out once installed in enhanced mode windows will only work in that mode unless you re-install it in compatible mode too.

---

