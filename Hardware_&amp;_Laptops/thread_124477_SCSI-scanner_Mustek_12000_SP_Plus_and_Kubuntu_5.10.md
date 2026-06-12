---
title: "SCSI-scanner Mustek 12000 SP Plus and Kubuntu 5.10"
date: 2006-02-01
forum: Hardware &amp; Laptops
---

### Post by dsamsonov on 2006-02-01
i have Kubuntu 5.10 (KDE 3.5 + apt-get update; apt-get upgrade)
also i have SCSI-scanner Mustek 12000 SP Plus (it's rather old model, i know). scanner was shipped with PCI SCSI card. i don't know model of this card, but it was shipped with scanner and on installation cd for windows there are drivers for Domex DMX3191 and they work with windows, so i think that i have DMX3191.

now i want to use this scanner on ubuntu. i tried to use SANE, but it can't help me.
as i know, at first i need driver for my SCSI-card, because in KInfoCenter at page "SCSI" i can see only two words: "Attached devices:". only two words, there are no any list of any devices. how can i help ubuntu to see this card?
at the [SANE]("http://www.meier-geinitz.de/sane/mustek-backend/index.html")'s site they say to do "sudo modprobe dmx3191", but it can't help me. moreover, they say "The driver for the DMX3191D is included in Linux 2.4.x."
however, in KInfoCenter at page "PCI" at one from the bottom position there are strange text:
```
0000:00:0c.0 SCSI storage controller: DTC Technology Corp. Domex 536
Flags: medium devsel, IRQ 16
I/O ports at e800 [size=32]
```
so i think that something like my SCSI-card ubuntu can see.

some internet sites say, that it have to work with this scanner and this card without any problems.
it works under windows, so i think that there are no hardware problem.

how can i solve this problem?

PS: sorry for my english, my native is russian. (-:

---

### Post by LordBug on 2006-02-01
Domex 536 is the chipset used on a DMX-3191D (according to Domex), so it's being seen correctly.  I would suggest running "sudo lsmod | grep dmx" and see if you see a dmx3191d entry.  Looks like you need to "sudo modprobe dmx3191d" to load it if it doesn't show up.

Beyond that, I don't know.

---

