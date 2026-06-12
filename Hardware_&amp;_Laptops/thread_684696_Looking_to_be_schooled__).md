---
title: "Looking to be schooled  :)"
date: 2008-02-01
forum: Hardware &amp; Laptops
---

### Post by incgnito on 2008-02-01
I have something that's bugging me a bit and I'd like to know if someone could help, and I'll probably put more in here than anyone needs but I figured I'd explain myself as thoroughly as possible so bear with me.

I just got off the phone with a friend who was having trouble with his D-Link DFE-500TX network card in Ubuntu 7.04 (using sundance module):  his problem was that his network card would stop working if he attempted to download anything of a significant size (i.e an OO update), however if he stuck with smaller stuff like just web pages it seemed to work okay.  After some of the standard troubleshooting steps I asked him what motherboard chipset he was working with which he couldn't answer exactly but we figured out that it was an older VIA chipset.  At that point I remembered a machine I had at one point (a first gen P4 rambus setup) that wouldn't boot to linux reliably unless you added "noapic acpi=off' kernel params to grub.  So on a hunch I asked him to add those params to his grub config file, reboot, and test his downloads again -- and lo and behold he can download whatever he wants now.

At this point I know what the fix is -- and apparently it's a common enough fix that it's listed as a standard boot menu entry in most LiveCD's I've seen -- what I don't know is *why* this is a fix.  What's actually going on and what does this fix do to correct the problem?  I know that I should probably just accept it works and be done with it, but the tech in me wants to understand better (i.e. I'm a glutton for punishment).  If anyone can explain it to me a bit I'd really appreciate it.

---

