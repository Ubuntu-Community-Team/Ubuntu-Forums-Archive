---
title: "Not detecting appropriate RAM value &amp; size"
date: 2009-08-18
forum: Hardware
---

### Post by sigixv on 2009-08-18
I have a freshly composed & install pc from today, only to notice the hardware is acting up for some reasons.

I have an asus P5QL Pro Mobo with 4x 1GB Kingston RAM modules KHX8500D2k2/2G DDR2 1066MHz Non-ECC CL5  5-5-5-15  2.2V

Freshly installed xp & ubuntu. XP install went fine. Ubuntu was slow to get to gui of the installer and failed a few times before actually getting to the gui installer (not the boot selector with the ubuntu logo). Finally got it to install & configure. Certain programs were acting up (amarok)  and i suddenly noticed system monitor said to have 3.2 GB of RAM instead of 4... Booted into xp, claimed to have 3.25 GB. Installed nvidia drivers in xp => short bluescreen & autoreboot; no fail dialog upon rebooting in windows though. Checked BIOS: affirms that 4096MB of RAM is installed, however @ 800MHz ! Selection of 1066 MHz is not available in bios settings, although supported by the mobo...

I found some win support forums where they claim it's a kingston-thing against the P5QL series. They were suggesting to install with only 1 module mounted with vista and then to upgrade to sp1 and all would be well :confused: Guess they suspect a divine intervention from vista healing the bios or something... They did mention that flashing bios didn't solve the issue.

Anyways, what do you guys suggest i do? Reinstall but this time with the xp on a different disk; try the vista fans' suggestion to install with only 1 RAM module loaded (however in ubuntu); a workaround with bios settings?;.... Al these problems only show themselves AFTER you have fully configured your desktop to your liking... :|

Al help greatly appreciated.

---

### Post by wolfe on 2009-08-18
The simple answer is that you need 64-bit versions of your OS's to be able to use that 4gig of memory.  32-bit OS's will only show 3.2gig of your ram, thats just an architecture limitation.  I'm willing to bet if you installed 64-bit ubuntu you would see all the memory present.

---

### Post by sigixv on 2009-08-18
Hadn't thought of that yet. Indeed, this is my first x64 enabled cpu i have so that might very well be the answer... Thx for the suggestion!
But it still leaves me boggled why the bios says my ram speed is 800 instead of 1066 MHz

---

