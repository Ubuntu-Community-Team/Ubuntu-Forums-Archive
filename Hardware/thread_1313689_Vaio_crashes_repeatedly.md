---
title: "Vaio crashes repeatedly"
date: 2009-11-03
forum: Hardware
---

### Post by bigjug_1991 on 2009-11-03
I've downloaded and installed Ubuntu 9.10 on a Vaio PCG-K76 (quite an old machine) about 10 days ago. The installation went fine and everything seems to be working fine. Except if I try to download anything it crashes. This is true for Update manager, software centre or downloading with Firefox.

When I checked the logs there are about 18 messages from glxinfo about problems freeing memory just before the machine locks up (doesn't restart just freezes). 

Is this a problem with the video card (Radeon Mobility 9200)? The video seems okay and I have no problem with screensavers or displays. It seems strange that it happens when downloading - I can browse the web without it crashing, but if I try to download a file then it crashes.

Please help.

---

### Post by Dark_Stang on 2009-11-04
What are the specs of the laptop? How old is it exactly? I can't even pull any documentation from sony's website on it.

---

### Post by bigjug_1991 on 2009-11-04
I bought it in 2004, and rather than chuck it away I reckoned Ubuntu might give it a few more years life.

It does still exist on the Sony site, but there is not much info:

[http://www.sony-asia.com/support/download/product/pcg-k76sp](http://www.sony-asia.com/support/download/product/pcg-k76sp)

From what I remember (I haven't got it with me right now) the specs are:

P4 3ghz
DDR ram (I've got 512 mb in, and it has a 1gb limit)
radeon mobility 9200 agp card
new-ish (2 years) samsung HDD - so that shouldn't be a problem

but I don't know any others - what would be useful to know?

---

### Post by Dark_Stang on 2009-11-04
Well, it's not as bad as I thought then. I was fearing a P3 and PC100/133 memory. But it sounds like you're having Kernel panics (a unix crash). That can be caused by faulty hardware. Have you tried running memtest and a hard drive test yet?

---

### Post by bigjug_1991 on 2009-11-04
No I haven't.

Memtest is from GRUB (esc when starting up?)

How do I test the HDD?

Thanks for the help!

---

### Post by Dark_Stang on 2009-11-04
Yes, Ubuntu comes with Memtest so you can run that from grub. For the HDD you'll want to download Samsung's diagnostic software. Most HDD manufacturers make this software freely available to download from their websites. Search Samsung's downloads section for diagnostic software relating to your hard drive's model. Hopefully they have a bootable disc as that is the easiest way to test.

---

### Post by bigjug_1991 on 2009-11-04
Memtest shows no problems, and the hdd is healthy.

If it helps the same machine ran win xp without problems.

---

### Post by bigjug_1991 on 2009-11-04
this is what the syslog shows just before a crash:

Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314558] glxinfo:1612 freeing invalid memtype e8102000-e8112000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314579] glxinfo:1612 freeing invalid memtype e8112000-e8122000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314597] glxinfo:1612 freeing invalid memtype e8122000-e8132000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314613] glxinfo:1612 freeing invalid memtype e8132000-e8142000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314630] glxinfo:1612 freeing invalid memtype e8142000-e8152000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314647] glxinfo:1612 freeing invalid memtype e8152000-e8162000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314663] glxinfo:1612 freeing invalid memtype e8162000-e8172000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314680] glxinfo:1612 freeing invalid memtype e8172000-e8182000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314697] glxinfo:1612 freeing invalid memtype e8182000-e8192000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314713] glxinfo:1612 freeing invalid memtype e8192000-e81a2000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314730] glxinfo:1612 freeing invalid memtype e81a2000-e81b2000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314747] glxinfo:1612 freeing invalid memtype e81b2000-e81c2000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314763] glxinfo:1612 freeing invalid memtype e81c2000-e81d2000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314780] glxinfo:1612 freeing invalid memtype e81d2000-e81e2000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314796] glxinfo:1612 freeing invalid memtype e81e2000-e81f2000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314813] glxinfo:1612 freeing invalid memtype e81f2000-e8202000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314830] glxinfo:1612 freeing invalid memtype e8202000-e8212000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314847] glxinfo:1612 freeing invalid memtype e8212000-e8222000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314863] glxinfo:1612 freeing invalid memtype e8222000-e8232000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314880] glxinfo:1612 freeing invalid memtype e8232000-e8242000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314896] glxinfo:1612 freeing invalid memtype e8242000-e8252000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314913] glxinfo:1612 freeing invalid memtype e8252000-e8262000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314930] glxinfo:1612 freeing invalid memtype e8262000-e8272000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314946] glxinfo:1612 freeing invalid memtype e8272000-e8282000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314963] glxinfo:1612 freeing invalid memtype e8282000-e8292000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314980] glxinfo:1612 freeing invalid memtype e8292000-e82a2000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.314996] glxinfo:1612 freeing invalid memtype e82a2000-e82b2000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.315013] glxinfo:1612 freeing invalid memtype e82b2000-e82c2000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.315030] glxinfo:1612 freeing invalid memtype e82c2000-e82d2000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.315048] glxinfo:1612 freeing invalid memtype e82d2000-e82e2000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.315065] glxinfo:1612 freeing invalid memtype e82e2000-e82f2000
Nov  4 16:58:40 Ubuntu-Sony-Laptop kernel: [   91.315081] glxinfo:1612 freeing invalid memtype e82f2000-e8302000

---

