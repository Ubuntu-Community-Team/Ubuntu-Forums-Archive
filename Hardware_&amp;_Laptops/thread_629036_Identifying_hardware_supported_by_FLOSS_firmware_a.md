---
title: "Identifying hardware supported by FLOSS firmware and drivers"
date: 2007-12-01
forum: Hardware &amp; Laptops
---

### Post by VCSkier on 2007-12-01
I'm going to be in the market for a new laptop at some point in the relatively near future, and I'm having difficulty identifying what choices would be best for the wireless card and the graphics card.

I know that I want a graphics card that will be able to use the new FLOSS radeonHD driver, but which cards do this, and which computer manufacturers use these cards?

Even more difficult has been trying to find information about wireless cards.  I know that the FSF recommends the use of certain Realtec and Ralink chipsets, but again, how can I tell which laptop manufacturers uses these chipsets?

I would consider system76, but they are still using Nvidia graphics cards, and I want to support ATi in their recent decision to embrace the open-source community.  Until Nvidia follows suit, I will never again buy a computer with a Nvidia card, therefore, no system76.

---

### Post by VCSkier on 2007-12-04
bump.

---

### Post by jocko on 2007-12-04
If you want a computer that works NOW, go for nvidia.
The [RadeonHD driver still only supports 2d]("http://www.phoronix.com/scan.php?page=article&item=931&num=1"), and the latest versions of ATI's proprietary drivers are very buggy.
If you absolutely want to use open source drivers, go for intel (but as you seem to aim at a high end radeon HD, you will probably not find any comparable intel gpu).
If you really think ATI is the way to go, it may be wise to wait a few months or even years until the drivers (open or closed source) are good enough to make use of the card (but by that time they will have released new cards, wich you will have to wait to get drivers for...).


As for wlan, I don't know much, but my laptop have an intel PRO/Wireless 3945ABG, which works fine out of the box (using the ipw3945 driver which is included in the kernel).

---

### Post by VCSkier on 2007-12-04
Would it be unreasonable to hope that 3D support would be ready on the FLOSS driver by Hardy +1(within a year)?  I know its very early in the game, but development seems to be going quite swiftly.

---

