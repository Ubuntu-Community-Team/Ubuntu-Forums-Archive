---
title: "Strange  problems since update..."
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by dizzylizard on 2009-04-20
Greetings, all!  I seem to be having a little difficulty with the latest automatic update...I got up this morning, and my box (an Acer Aspire 3680, Intel Celeron-M 1.66ghz cpu, 2gb RAM, connected via Sierra Wireless Compass 597 to Sprint mobile broadband) told me it had downloaded an important security update and needed to be restarted.  As it has been generally pretty good to me (once I figured out how to get the usb aircard working), I obliged its needs.  Now, the traitor has gone AWOL!  It shut down nicely, with no error messages that I saw, killed the power, and restarted.  That's when the problems started.  The cpu fan kicked on and the hdd started spinning up, and then stopped.  Black screen, no activity whatsoever.  Both fan and hdd stopped spinning.  Hard boot produced the same results twice, then the third time, all looked normal. BIOS gave me the standard memtest and device information.  Grub loaded, the ubuntu splash screen came up, then the login page...and that's when the second problem happened.  I had no keyboard or touchpad input. I dug out a usb keyboard and mouse, hooked them up and rebooted (after 3 MORE false starts and hard boots)...still no keyboard and mouse input.  I booted from the live CD (with the same initial boot problem...2 hard boots this time), and everything works just fine...on the live CD.  I got on the forums and did some searches, but none of the workarounds others have had success with worked...primarily because my internet connection doesn't "connect" until I get to the desktop...I see all sorts of workarounds that involve using apt to fix the Xorg.conf, but apt won't work without the internet connection...
My questions are three:
#1:  How do I fix these problems to return my box from its current state as a paperweight?
#2 For future reference, how do I start my mobile broadband connection from the terminal?
and #3:  If this happened during an "Important Security Update" is it a vulnerability issue, or just a typical GIGO bug?  By which I mean to say, did someone intentionally DO this to my computer, or was it just a corrupted update package?

I'm not a complete n00b, but I'm not very familiar with CLI's (unless you count DOS and C-64 BASIC), and I've been staring thru cracked Windoze for a long time, so long-winded explanations are greatly appreciated...I really want to learn what I'm doing "under the hood" if anyone is willing to take the time to nurture a baby penguin...
Many thanks for your time reading this post, even if you can't help!  Peace, love and Happiness

**EDIT: Changed thread title to better reflect problem...any help is greatly appreciated!**

---

### Post by dizzylizard on 2009-04-21
UPDATE: I've found the bug [on launchpad ]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/254840") and tried some of the workarounds there, to no avail.  I've booted older kernels, changed the priority of gnome, I've tried restarting X...nothing works!!!  HELP!!!  What's causing this?  I'm attaching my bootlogs (which I have NO clue how to interpret) in the hopes that someone can explain this to me!  Many thanks!

**EDIT: Ok...can someone tell me why my logfiles are invalid files? **

---

### Post by dizzylizard on 2009-04-22
bump

---

