---
title: "Installation Problems"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by istar9 on 2009-05-25
Ok, I have installed useing wubi fine before, But atm On This main computer I am haveing issues, and this one is the better specced out comp as well. 

System Specs:

AMD Phenom 9550 Quad-Core 2.2ghz
XFX MD-A72P-7509 Mainboard
2Gig DDR2 RAM
Nvidia GeForce 8600 GT

I have 3x SATA drives 2 Hard Drives and 1 DVD Writer, Not running IDE. Currently Have Win XP running fine. 

Have Tried:

Wubi with 30gig Space, Tried both Drives seperatly and a Few of the solutions given from older posts. All times was the 64bit Version of Ubuntu.

Given up on Wubi and Have Two Cd direct Installers. Wiped One drive out to have Ubunto Running on its own drive. 

CD versions 

9.04 64bit
8.04 64bit 

Have tried changeing bios SATA modes = Sata mode / Raid Mode / ACHI Mode (With Linux DID change) No Respones 

Each Time Ive installed this I go straight to Busy Box command line, with no errors above to see. I Do not know how to get rid of the splash screen to actually see whats going on ;/ ... 

Currently I am downloading the 32bit versions to see if there is any difference, but atm I just cannot find a solution to this.

---

### Post by istar9 on 2009-05-25
Tried the 32bit version of 9.04 no go.. My only thought is to try the 7.04 version in hopes that it can get somewhere. It sucks cause i was able to use this OS on the other comp, and made progress and now can't even get past the install process.

My firm belief is that this OS cannot see SATA drives correctly or has internal issues with them.

---

### Post by taurus on 2009-05-25
At the initial screen from Ubuntu LiveCD, press F4 to run it at a safe graphics mode.  Otherwise, use the alternate CD to install it.  Don't forget to burn the ISO image to your CD at a slow speed, not the default speed.  In fact, you should check the cd for defects at the initial screen too.

---

### Post by istar9 on 2009-05-25
ok thanks, will try the alternate CD next, have not tried any of those yet, and will put it at slowest speed. 

question would be, does version matter 64 vs 32bit to try ?

---

### Post by istar9 on 2009-05-25
Ok thank you for the input, this has gotten me much farther.. Seems the issue is that the CD works on boot up, but when going for the installation end, The CD is not found or mountable. 

It then sends me to the shell to look for the directory in /dev.. Which atm even using Shift page up, unable to find a match for the cd-rom ;/ Closest i saw was pkchdvd or some such, which did not work

Device is:
HP DVD Writer 1070r

spent the last hour or so scouring directories with the ls command.

---

