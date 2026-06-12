---
title: "Compaq Presario R4000 - The volume up/down buttons behave as if they're stuck."
date: 2008-12-28
forum: Hardware
---

### Post by diablo75 on 2008-12-28
I just finished installing Ibex on my brothers laptop with all the latest updates...for the second time.  The first time around I happened to install the kubuntu-desktop package, and I thought that some odd problems that I began noticing shortly afterwards was related to that package... but it wasn't.

After reinstalling Ubuntu and avoiding Kubuntu, the same problems would occur:

1.  Pressing the volume up or down buttons above the keyboard made Ubuntu act as if the user was holding that button down.  So pressing volume up would turn the volume up to 100%, but also continue to "press" the up button causing the volume level indicator to continuously appear like you were still pressing it.  Same would happen if you pressed the volume down button (volume shoots to zero percent, continues to act as if you're holding/pressing the button).

2.  After noticing this, clicking on just about anything on the screen seems very tricky.  Trying to click Applications/Places/System doesn't work.  You only appear to be causing a roll-over graphic effect by passing your mouse over top; clicking does nothing at all.

3.  This may or may not be related, but after installing the kubuntu-desktop package the first time around, the fast user switcher applet (in GNOME), which allows you to logoff/shutdown/restart/etc, would crash right off the bat.

That's about all I can say about the problem.  Any ideas?

---

### Post by diablo75 on 2008-12-28
Bump...

Also, I've found a few threads from others who are having this same issue.

[http://ubuntuforums.org/showthread.php?t=923947](http://ubuntuforums.org/showthread.php?t=923947)
[http://ubuntuforums.org/showthread.php?t=963722](http://ubuntuforums.org/showthread.php?t=963722)
[http://ubuntuforums.org/showthread.php?t=926608](http://ubuntuforums.org/showthread.php?t=926608)

And found a bug report, which describes the exact problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271706)

---

### Post by arron on 2009-03-02
I have a R4000 laptop too, with this same volume problem.  Is there any fixes out yet?

---

### Post by jetdog440 on 2009-06-02
I can confirm this issue, and I have a lot more information for whoever is pursuing this.

This issue is not ubuntu-specific - I have witnessed this in gentoo too (and likely affects them all, based on this bug).

I originally tried mapping the volume up/down keys to multimedia functions within gnome using XModMap within gentoo (basically creating aliases for special commands within Xorg), but then found the very same problem in gentoo - so I pulled off the keymaps and took a look for what was happening on keyboard input.

Fortunately, I was able to test a few more things within gentoo - but I can confirm that this issue is guaranteed to be from the same source as the problem within ubuntu.

I tried using xev, a program for watching input via event-based devices within xorg, and noticed that pressing either of the volume up/down keys on the R4125CA (R4000-series compaq laptop) causes one key signal while a volume up/down button is pressed, and the moment either of those is released, a completely different signal from the first is spammed endlessly - no other keypresses will stop this.

So, I tried using "showkey" from outside of Xorg, in a framebuffer console (basically command-line without gui ;)) .  Interesting, pressing and holding a volume up creates two seperate scan codes - something that I would imagine to be EXTREMELY quirky (and a terrible hack?).  I am not aware of any software for linux that will correctly interpret a double scan code.  But I suggest that the developers for ubuntu might be able to file this information with whomever would be responsible for dealing with this.

My locale and console region when dealing with this were EN-US and UTF-8.

As for the above issues of having the mouse pointer clicks not occuring - what I think I noticed was that following a volume key (for this device), a mouse click's signal is different, which explains why none of the mouse clicks after this event were working.

I would also like to point out that physically inside this system, it appears that the multimedia buttons are not directly part of the physical keyboard, though they might get combined via hardware later on (Which could be the real source of this mess - and software would be how windows *ahem* is dealing with this issue)

I can also confirm that this issue exists on the livecd.

Just as a suggestion: I believe it was the ZV-6000 (i think compaq) has similar internals to the R4000 - perhaps this issue should contain this information as well for whomever is trying to test it.

If ubuntu needs more debugging information, I will be happy to test this further, since I'm quite interested in fixing this for everyone -- because this issue has been present for a LONG time in every distribution, and these buttons USED to work fine (can't remember when -- possibly during kernel 2.4 ?).  Please reply if you want a complete log from showkey ouside of X.

Jet.

---

### Post by jetdog440 on 2009-06-11
Excellent, you'll all be happy to know that we have a fix in progress (reported working) for the Linux Kernel.

So far, the machines addressed by this patch include:
[LIST]
[*]Compaq Presario R4000
[*]Compaq Presario R4100
[/LIST]

We VERY-MUCH need anybody who has an **R4200** to visit the bug-launchpad page for this, because we have rumors that the R4200 is ALSO affected by this, and need confirmation.  All fixes will be submitted to the official Linux Kernel, and (unfortunately) you will have to wait until the next official Ubuntu release in October, in order to get this fixed in the new kernel image - 2.6.31.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/385477]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/385477")

For those wondering "why the wait until 9.10 Karmic Koala", Ubuntu has very-much stopped adding out-of-tree kernel patches, because they are too difficult to keep track of.  In any case if you are comfortable compiling/maintaining your own kernel, you are advised to test the patch from the above bug page, so we can hear of your successes ;)

---

