---
title: "Can I disable my onboard sound?  Problem with Virtualbox Sound."
date: 2009-02-10
forum: Hardware
---

### Post by Giggity on 2009-02-10
I've got a problem disabling my onboard sound since I want to use my Sound Blaster, and I think it's causing a problem with some of my programs.  I've set the "OnChip Audio Controller" setting in my CMOS to "Disabled," but Ubuntu still recognizes it.

So for some reason or another, Virtualbox is refusing to allow me to use my Sound Blaster 16 via ALSA.  I start up my new WinXP guest, and the Control Panel insists that there is "No Audio Device."  However, if I tell Virtualbox to use the onboard sound with the null controller, the WinXP guest recognizes it, but that's totally useless to me.

* UPDATE:  Turns out this isn't just a problem with Windows.  I installed a Linux Mint 6 VM and the same problem occurs.

Any ideas?  This is the first time this has ever happened to me.  I've used Virtualbox on the same computer before without this problem.  :confused:

---

