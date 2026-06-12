---
title: "NVidia GeForce Card problem"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by Stephen Shellard on 2009-08-21
I have just purchased an NVidia Geforce FX5200 128MB AGP Card in the hope of making some modest improvement to my computer.  

I fitted the card into my P4M800PRO-V1.0 motherboard, as per instructions re static etc.  I refitted the video cable to the new board and started up.  The screen was blank from the outset.  Returning the video cable to the original terminal made no difference.  Consequently I have removed the card and have reverted to my original system, which is working fine.

In an effort to get things moving I have done a couple of things, each time refitting the card to try out the changes:

[LIST]
[*]Upgraded the BIOS on the motherboard with a flash download.
[*]Tried resetting the BIOS for an AGP option.
[/LIST]

I noted a suggestion in one forum which was to  "disable integrated video in the BIOS prior to installing the card" but I can see no such option in my BIOS.

None of this has made any difference.  

POST SCRIPT I have now tested the card in another computer [which already had a graphics card fitted] and this has confirmed that the card *is working.*  I have now emailed ECS Elite Group Technical support - manufacturers of the motherboard, for advice on how to edit the BIOS of the motherboard in my own machine so that it will pick up the card.

PROBLEM SOLVED

I contacted the support for the motherboard who advised adjusting the voltage setting in BIOS for the new card on a trial and error basis.  I changed the setting from  0.05v to 0.8V  [there was also a .15V option].  This picked up the card first time.  I then went into System/Administration/Hardware Drivers  which immediately identified and recommended a driver for the card, downloaded it and installed it.

---

### Post by Shazaam on 2009-08-22
"I fitted the card into my P4M800PRO-V1.0 motherboard, as per instructions re static etc. I refitted the video cable to the new board and started up. The screen was blank from the outset. Returning the video cable to the original terminal made no difference. Consequently I have removed the card and have reverted to my original system, which is working fine."
"I noted a suggestion in one forum which was to "disable integrated video in the BIOS prior to installing the card" but I can see no such option in my BIOS."

Does your pc still run with the add-on card removed?
Does your motherboard have an "on-board" or "integrated" graphics chip?

When you look in your pc's bios it may be listed under "Integrated Peripherals" or "Onboard Devices". If it is a Dell pc it will be worded differently such as "Add-on Device".

---

### Post by Stephen Shellard on 2009-08-23
> **Shazaam said:**
> 
Does your pc still run with the add-on card removed?
Does your motherboard have an "on-board" or "integrated" graphics chip?

When you look in your pc's bios it may listed under "Integrated Peripherals" or "Onboard Devices". If it is a Dell pc it will be worded differently such as "Add-on Device".

[LIST]
[*]Yes, my PC runs with the motherboard removed.
[*]Yes my motherboard has an integrated graphics chip.  Here's some more details from the manual.
[/LIST]

[INDENT][I]P4M800PRO • High performance Northbridge with 1066 /800/533 MHz FSB
   (NB)     for P4/Celeron D processors
          • V-Link 533 MB/s high bandwidth North/South Bridge inter-
            connect
          • Integrated UniChrome Pro 3D/2D Graphics & Video Control-
            ler, Microsoft DirectX 9.0 compatible, OpenGL supported
          • Supports for AGP 8X/4X, AGP v3.0 compliant with 1.5V
          • Advanced 64-bit DDR2 and DDR400 SDRAM controller[/I]
[/INDENT]

It's a Zoostorm PC by the way.

Here is a link to some screenshots from my manual for the motherboard which seem most relevant.  [http://www.flickr.com/photos/carruchan/?saved=1](http://www.flickr.com/photos/carruchan/?saved=1)

Thanks for your attention. Much appreciated.

---

