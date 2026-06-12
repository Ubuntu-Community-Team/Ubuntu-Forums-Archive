---
title: "Dexconf created faulty xorg.conf when two video cards are installed"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by emeraldjay on 2006-12-19
I attempted to run the Edgy LiveCD on my Dell Dimension 2400 desktop only to come up with xorg not beign able to run. After going through both of the error screens I was able to come up with a cause and solution.

I have two video cards installed but only have a monitor hooked to the DVI output of my ATI card. the other video card is an onboard card with an Intel chipset. Dexconf is appently getting confused because while it was able to identify which PCI slot belonged to the card the monitor was hooked to, it incorrectly identified which card it was to be called.

It was naming the card Intel and used the i810 driver, when it should have named the card ATI and used the ati driver. After much cussing and swearing at the machine, I used the following as my solution:

Look through the /etc/X11/xorg.conf file for "i810" and replace with "ati" This trick only worked because xorg reported that the Intel card was on a different PCI slot from the one mentioned in the conf file. The slot mentioned in the conf file was actually the ATI card though dexconf configured it as if it was Intel.

I wanted to disable the onboard Intel card from the BIOS, but the BIOS only gives the options of "auto" and "AGP"

---

