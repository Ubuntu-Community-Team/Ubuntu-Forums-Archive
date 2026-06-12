---
title: "Is this laptop hardware profile compatible?"
date: 2008-11-15
forum: Hardware
---

### Post by damatta on 2008-11-15
Hi. I'm willing to purchase a notebook that ships with MS vista. I know not if it is compatible with ubuntu or xubuntu, can you help me?
Any comments, suggestions etc are welcome.

I'll post some relevant specifications as the original is not in english...:
NOTEBOOK L41SA 14POL T2130 MEM2GB HD120GB DVD-RW VISTA BASIC

Processor 	Pentium Dual Core T2130
                Clock 	1,86GHz Cache L2 1MB per core FSB 533MHz
Videocard       ATI Mobility Radeon X2300 HD (ATI M71), 128MB DDR
4 em 1 (SD/MMC/MS/MS-PRO
Firewire, S-Vídeo, Express Card tipo II, USB (x3)
Core Logic   	SIS 671 DX + SIS 968

Looks like it uses ECS. By the way, seems like the company behind the real production of this laptop is Hasee ( [www.hasee.com](www.hasee.com) ). Would you say this is something reliable? Because it has such a low price compared to mainstream products from dell, compaq, etc...

---

### Post by Yezinki on 2008-11-15
Yes it is.

---

### Post by damatta on 2008-11-15
Thanks! I had just found out it is compatible, however there are some procedures to follow prior to the installation.
I was instructed to run the live cd press <F6> and type:
live pci=noacpi noapic nolapic
Start installation and in a later stage the ATI 2300HD drive.
Now I'm confused as I was told the noacpi thing might hinder proper SMP functions. Does the aforementioned procedure impact my CPU performance or that noapic code is something temporary, a workaround to make Ubuntu start the live CD and nothing else?

---

