---
title: "BIOS settings for gigabyte GA-EP35-GS3P Mobo?"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by neatokino on 2008-02-04
I'm running 64bit Gutsy on a computer I've built with the Gigabyte GA-EP35-GS3P motherboard.  This is my first build, and as a Mac guy, I've never messed with a BIOS before.  The computer worked but wasn't entirely stable with the default settings.

I went and changed some of the settings that I thought were safe to change (partially based on settings suggested for this board in a 'Hackintosh' forum), and everything seems to be running better.  I'm not sure which of the changes helped, however, and I don't know if any of them are hurting.

Can anyone help me figure out what the optimal BIOS settings would be for this board to run Ubuntu?

btw, I turned off some of the thermal settings because I figured they were all connected to the Windows OS... is that a dangerous thing to have done?

Any help in determining the optimal BIOS settings would be greatly appreciated!

TIA
Michael

---

### Post by Existentialist on 2008-02-04
What type of BIOS settings were you changing? If you post the link to the hackigntosh thread it might help.  And as for turning off thermal settings, most of the temperature settings are for BIOS controlled fan speed and temp sensors.  Unless you are running software temp and fan controllers, I would recommend leaving the thermal settings at their defaults.

---

### Post by neatokino on 2008-02-04
This is the hackintosh forum with suggestions on changing the BIOS of the Gigabyte board for running OSX:

[http://forum.insanelymac.com/index.php?showtopic=83689](http://forum.insanelymac.com/index.php?showtopic=83689)

The changes I made to defaults were:

Enabled S.M.A.R.T. for the HD

Disabled CPU Thermal Monitor, Disabled CPU EIST Function, Disabled CPU Enhanced Halt

Changed HPET Mode to 64-bit (I'm only running Ubuntu 64bit on the computer, so this made sense-- I wouldn't be surprised if this was the only significant change I made vis-a-vis performance).

Enabled CPU Host Clock Control

Changed Performance Enhance from Turbo to STANDARD

Changed PCI Express Frequency from Auto to '100'

Changed Onboard SATA/IDE control mode from AHCI to IDE

I tried enabling the USB Keyboard and USB mouse, and that, oddly, affects everything badly.  I guess I'll need to keep a ps2 keyboard around just for making changes to the BIOS.

My system ran considerably faster and seems more stable after making these changes.  My CPU temperatures, according to lm sensors, are have not yet gone above 34C, but I am a little concerned about the thermal changes I've made.  I'll try re-enabling them and see if it affects performance at all.

Because these changes helped so much, I'm curious if there are other things to adjust.  I'm also curious to know what exactly I've done, but that would require far more knowledge than I can expect to gain.

Any suggestions?

BTW, if anyone cares, my system is a Gigabyte GA-EP35-GS3P motherboard, a Wolfdale e8400 3Ghz processor, 4GB Patriot 800 memory, a Gigabyte GeForce 8600 GTS video card (big heatsink and no fan-- I'm trying for quiet here),  WD Caviar 750GB HD, Samsung DVD burner.

---

