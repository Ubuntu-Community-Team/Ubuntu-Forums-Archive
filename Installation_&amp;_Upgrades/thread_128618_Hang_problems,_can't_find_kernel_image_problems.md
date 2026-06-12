---
title: "Hang problems, can't find kernel image problems"
date: 2006-02-11
forum: Installation &amp; Upgrades
---

### Post by idenr on 2006-02-11
Machine is a laptop IBM Thinkpad i1411 which has an E-IDE CD-ROM drive. The default install is hanging when it comes to "Loading module 'ide-cd' for 'Linux ATAPI CD-ROM'..."

When I tried "linux DEBCONF_DEBUG=5" it loads vmlinuz and initrd.gz and then prints "Ready." on the screen and just hangs there.

When I try "expert" it loads vmlinuz and initrd.gz and then clears the screen giving me a blinking underline cursor but just hangs there doing that forever.

When I tried "linux vga=771" it "Could not find kernel image: /install/vmlinuz"

What don't I know?

---

### Post by dcstar on 2006-02-12
[QUOTE=idenr]Machine is a laptop IBM Thinkpad i1411 which has an E-IDE CD-ROM drive. The default install is hanging when it comes to "Loading module 'ide-cd' for 'Linux ATAPI CD-ROM'..."

When I tried "linux DEBCONF_DEBUG=5" it loads vmlinuz and initrd.gz and then prints "Ready." on the screen and just hangs there.

When I try "expert" it loads vmlinuz and initrd.gz and then clears the screen giving me a blinking underline cursor but just hangs there doing that forever.

When I tried "linux vga=771" it "Could not find kernel image: /install/vmlinuz"

What don't I know?[/QUOTE]
Try: linux vga=771 noapic nolapic

That seems to help with some installs.

---

### Post by idenr on 2006-02-12
If I try to boot using "expert" or try "linux vga=771 noapic nlapic" the response comes back that it cannot find /install/vmlinuz. Basically anything I enter to the boot: prompt that starts with the word linux comes up with can't find /install/vmlinuz. Is there some other way of tricking it to find the boot program?

I think this has to do with the cd-rom drive not being fully recognized because when I try the live disk using "live-expert" I can get to the part where it tries to set up the cd-rom device drivers and it gets stuck. The cd model is a Sanyo CRD-S372B firmware 1.24. I don't know which dev to pick to load it and I'm basically unsure how to go about setting this up particularly if I can't get into expert set up mode.

Do I need to find a new driver to add to the set of drivers on the standard ubuntu install cd - one which will handle the Sanyo? Where would I go find such a thing if it exists?

---

