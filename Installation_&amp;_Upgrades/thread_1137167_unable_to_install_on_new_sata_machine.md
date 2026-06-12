---
title: "unable to install on new sata machine"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by starfry on 2009-04-25
Hi there,

I have just taken delivery of a new core i7 system (Asus P6T-Deluxe) that is 100% SATA (no IDE devices).

I have successfully installed Jaunty no problems but there are dependencies I need that are not available for it, so I want to install Hardy LTS.

However, it would seem that Hardy can't install from a SATA CD-ROM (you get an error "no common cd-rom drives found"), which is strange given that the machine does boot the Ubuntu install CD that is in the very same drive.

I attached an IDE CD-ROM just to test. That worked but then no hard drives were found. As all these are SATA I draw the conclusion that for some reason SATA is not supported by the installer.

In both cases above I have tried the Alternate install CD.

I would have thought the latest LTS version would support SATA. Are there any resolutions to this problem available ?

---

### Post by sandbird on 2009-04-25
Linux not supporting SATA at all - it's a known problem.
Install on IDE or use VMWARE inside Windows.

---

### Post by autocrosser on 2009-04-25
Not exactly correct--I'm on a i7 920 unit with SATA only & I have several installs going. You need to go into your BIOS & start your SATA devices as legacy IDE--if you run everything as hot-plugged SATA you can't install...By the way--the i7 with Jaunty is blazingly fast!!!

---

### Post by starfry on 2009-04-25
It doesn't work for me with legacy IDE or AHCI. My machine was originally set to Legacy IDE.

I have got it installed with Jaunty, no problems at all. My issue is caused by wanting to run openVZ which is only supported on Hardy LTS. I really need to find a way to get Hardy installed...

---

### Post by autocrosser on 2009-04-25
The only other thought I would have is to buy a IDE PCI card that is supported by Linux--Not sure I can help you there....

---

### Post by starfry on 2009-04-26
thanks, I have it installed using Hardy Desktop (could not get it to work with the alternate CD). I had to add a kernel parameter all_generic_ide.

---

### Post by autocrosser on 2009-04-26
Good to hear--How are you liking the i7?  I've had mine for about 3 months now--running stable @ 3.5GHZ using a Zalman 9700 for cooling--with BOINC using all 8 cores my temps are running in the low 60c range. My BOINC scores have gone thru the roof :P

If you look at the bottom of the first post on this link: [http://forums.tweaktown.com/f69/gigabyte-latest-bios-28441/](http://forums.tweaktown.com/f69/gigabyte-latest-bios-28441/)  There is a couple of good .pdfs about O/Cing the 920...Very different from the older Q series.....

---

### Post by starfry on 2009-04-26
autocrosser - hate to make you turn green but my Core i7 920 is a D0 stepping and is overclocked to 4Ghz!!! I'm only on my second day but like it so far. The only problem has been Ubuntu, and I really hate saying that :(

I am determined not let Microsoft near this new machine, except in a carefully contriled virtual machine :)

---

### Post by autocrosser on 2009-04-26
NA--it's cool--I tend to O/C on the safe side & a 1GHZ O/C over stock works very well for me--I had it running at 4.1 a couple of days after I got it, but the temps were a bit much for me so I went to a lower number that "should" be good for the long-term.... I was a "early-adopter" & got a 920 as soon as it was available--I'm waiting until the new Intel releases to step up to a 940 or newer.

What Memory are you running?  I've got G-Skill 9-9-9-24 1600 right now--thinking about 2000 stuff--My Gigabyte M/B will run up to 2100 on mem multi...

Hang in there with Ubuntu--I've been with it from the very early days & each update has been better..If you are interested, the Karmic (9.10) testing group will be starting up in about 2 weeks or so--I really like the "over-the-bleeding-edge" testing & start with the new group before alpha1---You might look in from time to time--about alpha 4 or 5 things start getting stable for the next release & you get to play with all the shiny new toys ;)

---

### Post by starfry on 2009-04-28
I have it running now with Hardy Desktop (I could not get the alternate CD to work at all). The desktop CD worked but needed a kernel parameter "all_generic_ide".

The problem is I now have bloat that I don't need that I will have to uninstall at some point. At least it's installed though,  - I have HArdy 64 bit with OpenVZ up and running :)

---

