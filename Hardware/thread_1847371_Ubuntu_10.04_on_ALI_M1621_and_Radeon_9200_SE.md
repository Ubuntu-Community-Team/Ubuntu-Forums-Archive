---
title: "Ubuntu 10.04 on ALI M1621 and Radeon 9200 SE"
date: 2011-09-20
forum: Hardware
---

### Post by chrwl on 2011-09-20
Hi everyone

Installed Lucid on a 8GB Sandisk CF card in a PII 350 MHz PC with 512 MB RAM, PCChips M726 (ALI M1621 / ALADDiN-Pro II chipset) and MSI Radeon 9200 SE AGP graphics card. Didn't have much luck getting it to run stably, since there were problems accessing the drives in the PC.

Appended libata.force=dma2 and pata_ali.atapi_dma=1 to grub.cfg. This solved the drive access problem, but it would still crash intermittently and have graphical corruption when booted and displaying the desktop. Disabling modesetting (which helps with my GMA950 adapter in my laptop) worsened the symptoms.

Read through the Xorg logs and saw that the card automatically selected AGP 2x, which has always caused problems in Windows XP. This also caused the card to restart internally (according to the log) and disable hardware acceleration. Forced the card into AGP 1x mode at startup using radeon.agpmode=1, and the problem was solved.

I know this is not so much a question as a solution, but I thought I'd post it anyway for the benefit of anyone else that might have this hardware combination.

Genius serial mouse was fixed by adding inputattach --intellimouse /dev/ttyS0 to my /etc/rc.local file. Now I just need to figure out how to get the DIN connector keyboard working reliably. Not that I would mind upgrading to USB, since the keyboard has seen better days :lol:.

---

