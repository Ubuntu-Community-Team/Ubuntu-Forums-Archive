---
title: "&quot;CD-ROM won't mount&quot;"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by d_demchuk on 2006-02-04
Hi all,

I'm new to Linux (trying to leave Windows behind) and have just purchased a new computer with the hopes of running Ubuntu on it. I started to install Ubuntu and got as far as the detection of the CD-ROM drive--but then got a blue screen for quite a few seconds and then a message saying that the CD-ROM wouldn't mount--likely because the CD-ROM was not in the CD drive. This was not the case, but I opened and closed the drive hoping that things might improve. No such luck--a somewhat longer blue screen and then the same message. I couldn't get any further than this.

I am pretty sure the drive is Ubuntu-compatible--it's a Pioneer 110D DVD/CD drive. I tried burning a second image from the ISO and running from that. Same problem. Any suggestions?

Thanks,

David Demchuk
Toronto, Canada

---

### Post by taurus on 2006-02-04
Just how fast were you burning the ISO image?  Have you tried burning it at a slower speed like 4X???

---

### Post by d_demchuk on 2006-02-04
Just tried burning a 4x disc...same problem. (And a Ubuntu Live disc I burned and ran on my previous computer comes up with the same error message on this one.) I'm going to tinker with a few things to see what I can find out.

Thanks,

David

---

### Post by taurus on 2006-02-04
Maybe want to check the connection on the back of the CD drive then...  I assume it is an IDE drive, right!

---

### Post by d_demchuk on 2006-02-04
Well, just tried switching the old cd-rom drive (a four-year-old Sony) for the new one (the Pioneer) and running the Ubuntu cd--same error as before. 

The screen before the error is when the hardware/CD-ROM is being searched for--the loading bar briefly pauses at 77% and reads "loading module ide-generic - linux IDE support" and then scoots through to the end. 

I tried booting with "linux noapic and nolapic"--when I did this, there was no pause at 77% but at 86% ("loading module ide-cd for linux atapi cd-rom") the machine hung up and I had to reset.

I'm running:
Asus 915G motherboard - Socket 775, Dual Channel memory, PCI-Express, Ultra-DMA, etc.
Intel Pentium 4 630 3GHz processor
ASUS GeForce 6800GT 256MB PCI-Express video card
Seagate 160GB hard drive
2x512 DDR RAM
and a bunch of other things that, hardware-wise, shouldn't matter.

The aforementioned Pioneer DVR-110D (ATAPI device (ATA-5 & SFF-8090 Ver 5, PIO Mode 4, Multi Word DMA Mode 2, Ultra DMA Mode 2, and Ultra DMA Mode 4 (Ultra DMA 66) - currently set to "auto" in the bios)

Bios is AMIBIOS - enhanced IDE mode support is on - SATA+PATA

Thanks,

David

---

### Post by d_demchuk on 2006-02-04
A little more info:

I just tried using Instlux to install Ubuntu from the internet (bypassing all questions about my drives entirely)...I actually got quite far this time--through downloading all of the packages and at least 60% into installing them...

..but then the screen went white, filled with repeated text: numbers counting down one side endlessly with the same message on each line--
"hda: cdrom_pc_intr: the drive appears confused (ireason=0x01)"

I feel like I'm getting much closer to the solution...but any thoughts or suggestions would be helpful. 

Thanks again,

David

---

### Post by d_demchuk on 2006-02-05
Could it be because my hard drive (the Seagate 160 GB) is SATA and is the master on the first channel, and my DVD drive is EIDE and is the master on the third channel? Would that cause the confusion that the install process is complaining about?

Just another thought,

David

---

### Post by d_demchuk on 2006-02-05
Me again...it turns out that the problem was that I had SATA + PATA indicated in the IDE section of my Bios, when it should have been set just to SATA. Now everything's working well, and I'm enjoying Ubuntu the way it's meant to be enjoyed :)

Cheers,

David

---

### Post by anil_robo on 2006-03-01
[quote=d_demchuk]A little more info:

I just tried using Instlux to install Ubuntu from the internet (bypassing all questions about my drives entirely)...I actually got quite far this time--through downloading all of the packages and at least 60% into installing them...
...
David[/quote]

Hi David

I can see you were determined and you succeeded in installing Ubuntu from internet. I want to do the same: Can you tell us how did you do it?

Thanks

---

