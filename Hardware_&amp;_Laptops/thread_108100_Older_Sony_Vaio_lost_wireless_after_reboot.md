---
title: "Older Sony Vaio lost wireless after reboot"
date: 2005-12-25
forum: Hardware &amp; Laptops
---

### Post by crystalattice on 2005-12-25
I have a Vaio laptop PCG-FRV35.  I'm trying to figure out if my wireless problems are due to the computer itself, the PC Card, or if it's a software issue.

At the beginning of this year I had SuSE 9.1 installed and my D-Link wireless card was working.  I wanted to try a different distro but couldn't get the card to work so I went back to SuSE.  However, I could never get the card to be recognized again; ndiswrapper would show the driver installed but no hardware present.

Two days ago I went ahead and installed Ubuntu after reading about a successful laptop install on O'Reilly.  Initially everything worked great; the wireless card was detected the first time and I was able to get everything working.  Just to make sure, I rebooted the computer to make sure it would work again.  Ha ha, the joke was on me.  Now only the built-in ethernet and modem are detected; the wireless card doesn't even appear in the Network panel.

I reinstalled Ubuntu since it had worked after my first install, just to help troubleshoot, but it didn't work.  The D-Link card isn't detected by Ubuntu at all.  I manually installed ndiswrapper this time and followed the tutorial on the wiki but I'm having the same problem I did w/ SuSE:  the card's driver will install but the hardware isn't detected.

I have XP installed on a dual-boot.  XP will let me use the wireless card for about 10 minutes then it locks up, hard.  I can recreate it at will whenever I'm web surfing via wireless; using my ethernet port, I have absolutely no Internet problems.  Same w/ Ubuntu; I can network via ethernet but not wireless.

This is a replacement card from the manufacturer and since the card works initially, I don't believe the card is at fault.  I'm also using the latest drivers from the D-Link website so I doubt that's the problem.  Right now I'm thinking the computer itself, or at least the PC Card connectors, are jacked up and no amount of software tweaking will fix it.

Does anyone know of a good way to confirm this?  I don't own any other PC Cards so I can't test other cards.

---

