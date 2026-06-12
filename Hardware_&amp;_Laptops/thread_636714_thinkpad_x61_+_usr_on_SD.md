---
title: "thinkpad x61 + /usr on SD"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by fixture on 2007-12-10
due to the lame HDD+power management issue in Gutsy, I was trying to get a work around and reduce HD use.

Because thinkpad X61 has a Ricoh SD/MMC slot, and the fact I have some 2G SD non-SDHC cards around, I am trying to put the entire root on the SD card. 

05:00.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)

But the basic Gutsy is over 2Gs, so I just put the /usr dir on the SD, ext3, read-only. /tmp is configured to mount as tmpfs, no swap. Compiled vanilla kernel 2.6.23.9 with gutsy stock configuration to include mmc as a part of the kernel rather than as a module.  I figure that whatever the OS needs to write is still on the HD, so I didn't fix anything else.

Everything works, boots slightly faster, except that the X61 does not come back from suspend, console and gnome both appear blank, though I can see mouse pointer on gnome and nothing else. (this is a reproducible problem, as soon as I remount /usr to the one on the HD, suspend problem disappears)

Thinkwiki ([http://www.thinkwiki.org/wiki/Problems_with_ACPI_suspend-to-ram](http://www.thinkwiki.org/wiki/Problems_with_ACPI_suspend-to-ram)) claims to have a similar mmc semi-reproducible error with a fix under "Built-in MMC reader" except that it's not reproducible on stock kernel. Didn't try this on 2.6.23.9 because I don't think there is anything significant going into it, and did not feel like recompiling the mmc part into modules.

after looking through this, am I making wrong assumptions? is the OS writing to /usr? or is it simply that MMC part of the kernel sucks?

---

