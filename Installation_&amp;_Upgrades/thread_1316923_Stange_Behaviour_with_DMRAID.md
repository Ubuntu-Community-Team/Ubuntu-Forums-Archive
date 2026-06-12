---
title: "Stange Behaviour with DMRAID"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Cr0n_J0b on 2009-11-06
I'm just posting this to try to understand what is going on with my system.

I have an Asus A8N-SLI Deluxe motherboard with 8 onboard SATA ports.  Add to that, I have another add-on SATA card with 4 more ports.  the SATA chipsets are SIL and Nvidia.

I have 3 500GB SATA drives all the same.

I attach one to the Nvidia ports and boot from the install disk with the nodmraid option.

This works sometimes and not others.  When it works, the install partitioner finds the drive and i'm all good.  when it doesn't work, no drives show up in the partitioning screen.

I can then go back, boot liveCD (nodmraid) and see all the partitions in gparted or disk tools.  so I know the OS can see them...but when I install from liveCD...the partitioner again shows nothing for available drives.

In experimenting, I figured out that if I use a brand new drive, than hasn't been installed to, it will show up properly...but not drives that i have tried to install on in the past.

My theory is that the partitioner looks for drives with no MBR to use for the install.  Does this make sense?  If so, how do i "clean" my devices so I can install to them?

thanks

---

