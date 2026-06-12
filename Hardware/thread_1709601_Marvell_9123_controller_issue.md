---
title: "Marvell 9123 controller issue"
date: 2011-03-18
forum: Hardware
---

### Post by TomB19 on 2011-03-18
Hi.

I had been having miserable problems with a pair of SiI 3132 - 2 x eSata PCIe 1x cards.  They were silently corrupting data on a pair of 8 bay external SATA cages that use port multipliers to connect 8 drives to the PC using 2 eSATA cables.

I picked up a pair of Marvell 9123 based cards.  They were said to be the real deal.

The 10.10 kernel picked up the controllers and recognized them immediately but I can't see one drive in each cage.  I've tried swapping in different, known working, drives but they don't show up at the OS level.  Each card's BIOS recognizes and displays the drives on boot without fail.  If I swap back to the SiI 3132 controllers, it will pick up all drives at the OS level.

I think this is an issue with the Marvell driver as it is built into the kernel.

I can't figure out how to configure the cards for ATA, instead of ACHI.  It shows they are configured for AHCI in the BIOS but there doesn't appear to be a way to change it.  If I do that, I think I'll loose the port multiplier capability, anyway.

I haven't read too many issues with Marvell 912x controllers but they're fairly new.  Maybe there aren't many of us using all the features like port multiplication, etc.

Is anyone else having issues with a Marvell 912x card?  I think the 9123 and 9128 are pretty much the same card with the 9128 having a RAID5 feature not found on the 9123.  I would imagine they take the same driver.

By the way, hard drives are advanced format WD (WD20EARS).  Yes, I know they aren't designed to be a RAID drive.

Any ideas?  Any recommendations?  I need 4 x eSata ports to connect to a pair of port multiplier based external chassis.  I'd certainly pick up different controllers.  The thing is, I did a bunch of research before going with the Marvell based cards so I'm surprised they aren't working perfectly.

I should mention I'm running x86_64.

Thanks!

---

### Post by JGSD on 2011-05-30
This isn't exactly the same problem I'm having because my Marvell 9123 controller is integrated into my ASUS P6X58D-3 motherboard, but the end result is the same: Ubuntu doesn't seem to like this controller!

If I go into the Marvell BIOS I am able to create the RAID array and, as you mentioned, it only shows as ACHI mode. I can't change this from the Marvell BIOS either. However, in the regular Asus BIOS, I can toggle between ACHI and IDE.

If I choose IDE, the drives show up separately during the Ubuntu installation. If I choose ACHI, Ubuntu correctly identifies it as a RAID array and installation completes without any issues.

The only problem is that after the system reboots, it doesn't even seem to get as far as GRUB! I get a black screen with a flashing cursor and that's it!

I'm trying this with 10.04 LTS Server x86_64 but I've also tried with 11.04 Server x84_64 and 10.10 Desktop just to be sure but the same thing happens every time.

You'd have thought that the fact that Ubuntu recognizes the RAID array and proceeds with the installation would mean that the Marvell 9123 controller is properly supported, but the failure to boot says otherwise.

---

### Post by TomB19 on 2012-02-08
I'm updating this thread for the benefit of others who are up against the same issue.

This issue was fixed by a firmware update.  Particulalry FW 1701.

The two firmware releases newer than 1701 brought with them their own problems.  Particularly, they wouldn't work with the Si port multiplier due to a "vendor incompatability".

Ultimately, I switched back to a pair of Si3132 cards to drive my two drive enclosures.  This is where I started.

The key to Si3132 cards is to get a recent chip.  Several versions exist and they all have bugs but the most recent chips aren't too bad.

Ultimately, if you want stable eSATA with stable drive multiplier support, get a SATA to eSATA breakout plate for your motherboard ports.  That's the only way to be completely free of the bugs and minor glitches.

---

