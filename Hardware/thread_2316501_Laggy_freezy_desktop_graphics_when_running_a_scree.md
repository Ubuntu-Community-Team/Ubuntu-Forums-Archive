---
title: "Laggy freezy desktop graphics when running a screen of a second card."
date: 2016-03-08
forum: Hardware
---

### Post by noocnoom on 2016-03-08
I've got an issue where I have janky freezy graphics just when on the desktop with nothing open.  If I move my cursor around, it'll freeze every 20 seconds or so for a few seconds.  If I move it over to the other screen, it'll freeze when the cursor is right in between the two for a moment.  Menu animations are freezy.  Also the second, weaker card is really using it's fan when all it's doing is showing a desktop.

It's not like it's constantly treacle speed, it's fine for 20 seconds, and completely frozen for 5, though exact numbers vary.  And it always lags when I go from the right screen to the left, right bang in the middle.  Also, input doesn't freeze.  My mouse movements during freezes have been done when the freeze ends.  If I play a flash video, it keeps playing fine under the freeze, and I can hear it.

Here's what I'm running:

Intel i7 2600k with 16 GB RAM and an SSD.
Radeon R9 390 8 GB in main PCIe slot with a 1440p screen plugged in via DisplayPort.
Radeon HD 5770 in second PCIe slot with an 1152p screen plugged in via VGA.

Here's what I've tried:

Removing all non-essential hardware, including integrated peripherals in the bios.
Swapping Ubuntu 15 for Linux Mint 17.3 Cinnamon, and Linux Mint 17.3 Mate.
Swapping the 5770 for a Geforce 210 (which has no fan, but is getting quite hot).
Swapping for lxde, and openbox, and using software rendering on Mint (don't know how to do that on Ubuntu).
Swapping for all different driver combinations on all these cards.
Taking all these cards and installing Ubuntu and Mint on a completely separate, though still quite powerful base unit.
All of the of the above in every combination (I think I've tried every single combination of OS/card/mobo/etc at this point).

None of these have any impact on the laggy freezy jankyness, some of them brick the machine (certain drivers break X).

Here's what I've tried that actually impacted it:

Running both screens drastically under their native res.  The lag is considerably lessened but still there.
Running MS Windows.  Everything works great (this has been a long time Windows setup - never had any performance issues until I moved to Ubuntu).
Only running one screen via the main card (the R9).  Everything works great, even at 4k (the screens native res, but not the one I intend on using).

None of these fixes are actually fixes though.  The goal is to get both screens running on two cards (because the second screen can't run of the main card) on Ubuntu 15 at the desired resolutions.

Any suggestions would be greatly appreciated.

---

