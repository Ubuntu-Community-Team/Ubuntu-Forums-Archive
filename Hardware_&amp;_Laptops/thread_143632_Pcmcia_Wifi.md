---
title: "Pcmcia Wifi?"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by morpheus2485 on 2006-03-12
fresh install of kubuntu, on a dell laptop and everything works but the pcmcia wifi card.  I've never worked with them under linux before so i'm not sure where to start.... in case you ask here's the gist of some interesting lspci output (i can't copy and past because the laptop has no built in networking interfaces)

Network controller: RaLink: Unknown device 0301
Host Bridge: intel Corp. 440BX/ZX/.....
PCI bridge: intel corp. 82371ab/......

ifconfig gives nothing but the lo

i'm thinking the module for the pcmcia port isn't up.  which module might it be?

---

### Post by Zelut on 2006-03-12
I would suggest checking out posts concerning ndiswrapper for your wifi.  I have set it up on a few pcmcia based cards and it works just as well as PCI or on-board.  Maybe take a look at the linux wifi page in my sig & see if that helps you get started.  Searching the forum for other ideas also helps a lot.

---

