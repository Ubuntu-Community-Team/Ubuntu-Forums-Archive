---
title: "Sherlock Holmes req: Wont mount root partition+"
date: 2010-08-16
forum: Hardware
---

### Post by siabost on 2010-08-16
Hi,
Dell Dimension 2350 - P4 2Ghz
[http://support.euro.dell.com/support/edocs/systems/dim2350/specs.htm#1101572](http://support.euro.dell.com/support/edocs/systems/dim2350/specs.htm#1101572)

First of all wouldn't boot with certain PCI Wireless cards fitted:
Netgear Wireless Card - OK
Belkin Wireless Card - no boot
D-Link Wireless Card - OK

Since loading Ubuntu 10.04 I've been getting Video collapses - flashing vertical lines on a black screen - which I put down to a dodgy Intel 845G/GL Integrated Graphics chip.

As the PC does not have an AGP slot I bought a PCI Graphics Card (PNY nVidia 8400GS 512Mb DDR2). With this in place, Xubuntu 10.04 installed & the BIOS switched from "onboard video" to "auto" I first got an error stating "low end corrupted memory" & later, on another attempt, a message saying the HD root partition had failed to mount.

Ubuntu live CDs fail also - see attached screenshot.

I tried to reinstall with an alternate Xubuntu CD & it fails while attempting to mount the root partition.

Thinking it might be faulty memory causing the problem I tried the following:
With 512Mb installed - the alternate installer gets as far as trying to detect my network hardware and freezes at 0%.
With 768Mb - we get as far as 2% on network hardware detection.
With 1024Mb - it rattles through the network hardware detection, HD partitioning then fails to mount the root partition to begin the install.

Is it worth buying some brand-spanking new memory for it or am I throwing good money after bad?

Absolutely any help appreciated:)

Edit: The BIOS has been updated to the latest available (A02)

---

