---
title: "PCMCIA Wireless card doesn't power down"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by Fluffykins on 2009-11-11
Just managed to install Ubuntu 9.10 on a Tosh Sat Pro 4600 (Clean install)

I still have the problem that the LED on the Netgear WG511T PCMCIA wireless card (Atheros chipset) stays on after shutdown.

I can force the LED to go off by removing and reinserting the wireless card after shutdown, but that's just a little inconvenient and not family friendly.

Does anyone have any ideas how to make shutdown work properly?

I only had a couple of other problems with the install - both seem to be sorted:

Created/Edited xorg.conf to give 1024x768 resolution on the screen, instead of 800x600 max (Why oh why not have all valid screen resolutions available "out of the box"?)

Edited S40umountfs to cure the problem of no power off when shutdown requested (see [http://ubuntuforums.org/showthread.php?t=1317890](http://ubuntuforums.org/showthread.php?t=1317890)) - Not having this work properly out of the box seems a major omission!

Many thanks in advance.

Fluff

---

### Post by Fluffykins on 2009-11-13
Bump:popcorn:

---

### Post by Fluffykins on 2009-11-15
Problem gone away for a bit. I just reinstalled U9.04 and the card powers down nicely.

Strange 9.10 didn't work properly.

If anyone does come up with a solution that works in 9.10, I'd like to hear.

---

### Post by The Spy on 2009-11-23
I've got a similar problem. I've got an Apple Powerbook G4 with a Broadcom wireless chipset. When I have the drivers installed my system will not shutdown, but I remove them it shutsdown just fine. I'm still looking into this problem too.

---

