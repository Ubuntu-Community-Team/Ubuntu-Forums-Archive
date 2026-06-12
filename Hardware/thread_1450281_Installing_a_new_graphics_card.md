---
title: "Installing a new graphics card"
date: 2010-04-08
forum: Hardware
---

### Post by icedawg3352 on 2010-04-08
[SIZE=2]I am going to be installing a new graphics card. the card is a[/SIZE][SIZE=2] GeForce FX 5200 256MB 128-bit DDR PCI. 
can anyone give me simple instructions to install this?[/SIZE]

---

### Post by emanuel.b on 2010-04-08
Do you mean complete instructions, or just how to install the drivers afterward?

---

### Post by Fafler on 2010-04-09
Disconnect the power chord, insert the card in a PCI slot. Connect the monitor to the new card, re-connect the power, boot. When you boot into Ubuntu it will use the free nv driver. To get full 3D support, you need to go to System -> Preferences -> Hardware Drivers and install the binary nvidia driver from there. Note that you need the older legacy driver and not the latest release from nvidia. From the back of my head, i think 173.xx is the last version to support the FX5200. But Ubuntu should figure that out automatically.

---

