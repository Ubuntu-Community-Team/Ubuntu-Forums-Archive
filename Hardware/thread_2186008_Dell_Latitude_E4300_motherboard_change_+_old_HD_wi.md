---
title: "Dell Latitude E4300 motherboard change + old HD with dual-boot (12.04 and XP)"
date: 2013-11-05
forum: Hardware
---

### Post by bulat_zag on 2013-11-05
[COLOR=#333333][FONT=Trebuchet MS]Dear All,
[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]I have a Latitude E4300 laptop with P9400 CPU, A24 BIOS and a SATA 160 gb drive and 2x2 gb RAM. The systems is dual boot with Ubuntu 12.04 (main OS) and XP professional (secondary OS) on the same drive but on the different partitions. My old motherboard seems to have gotten fried last night - laptop boots up to the Grub, but keyboard is unresponsive and nothing happens until I power it off. I also cannot run any pre-boot diagnostics or enter bios, since keyboard is unresponsive from the begining. I tried re-setting RAM sticks, unplugging and booting up without keyboard, trying an exernal USB keyboard, all to no avail. Which led me to believe that it is a mb issue.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]Now, as a solution I d like to get the same model motherboard off ebay and simply swap it, while preserving the HD configuration. I was wondering if 
[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]a) it is going to work [/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]b) what should I do with BIOS, since a new motherboard will not have GRUB installed.[/FONT][/COLOR]
[COLOR=#333333][FONT=Trebuchet MS]thanks![/FONT][/COLOR]

---

### Post by Bashing-om on 2013-11-05
bulat_zag; Hey, that is tough !

May I suggest before swapping out that motherboard, pull the battery and check it (volt meter) , these batteries only last so long. Or maybe just go ahead and replace the battery ?

In the event the MB has died,;

Swapping it out will have minimal affects to the operating system installed.
Set in bios on that new MB to boot the primary operating system and should be good to go.

grub is not a part of bios, setting the boot priority in bios tells bios where to look for the boot code. That boot code is installed onto the hard drive - MBR sector if booting using legacy partitioning on the hard drive.

[INDENT][INDENT]my best wishes
[/INDENT][/INDENT]

---

### Post by bulat_zag on 2013-11-05
Bashing-om, you gave me hope! 

and thanks for clarifying about the location of the grub, I was sure some magical chip exists on the motherboard that has all the info about the installed systems!

---

### Post by Bashing-om on 2013-11-05
bulat_zag; Sure thing !

Let us know how it goes.
[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

