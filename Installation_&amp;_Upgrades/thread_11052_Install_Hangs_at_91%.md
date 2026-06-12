---
title: "Install Hangs at 91%"
date: 2005-01-13
forum: Installation &amp; Upgrades
---

### Post by Boiler98 on 2005-01-13
Hello all.

I'm giving my first Ubuntu install a go, looking to replace with my Gentoo install with something a little more my speed for my needs. :)

During the install I get the first progress bar, "Detecting hardward to find CD-ROM drives" appears at the top, gets to 91% and then freezes.  The message at the bottom reads "Loading module 'sd_mod' for 'SCSI disk support'...".

My system is a Shuttle SB75G2 PC, with a SATA hard drive.  All the specs/chip set info can be found here: [http://global.shuttle.com/Product/barebone/brb_OverView.asp?B_id=23](http://global.shuttle.com/Product/barebone/brb_OverView.asp?B_id=23)

In the past, when installing Gentoo, I used a Knoppix CD to boot the system and installed the base Gentoo system from there.  Knoppix detected everything w/o any trouble so I'm not sure what I might need to do to get things working.

Thanks for any help!

*Edit:*
I'd also like to use the upcoming release, which supports X.Org instead of XFree.  What are the steps I should go through in order to use it once I get past the install. :)

---

### Post by r3m0t on 2005-01-13
I'm having the same problem. :confused:

---

### Post by Boiler98 on 2005-01-13
R3m0t, can you post your system setup?  Maybe we can find a common thread.

---

### Post by Boiler98 on 2005-01-15
I found the module that is causing the problem:

ata_piix (Intel Corp. 82901EB (ICH5) Serial ATA 150 Storage)

This module will attempt to load 'sd_mod' which will, in turn, lock up the installer.

Can anyone think of a solution to this?  Since I am working off an SATA drive (which is my only drive, and switching to IDE is not an alternative) it would seem that this is a major show stopper.

Thanks for any help.

---

