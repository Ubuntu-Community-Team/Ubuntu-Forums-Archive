---
title: "Install Dual-Width GPU with only 1 PCIe slot. HOW!?"
date: 2014-12-29
forum: Hardware
---

### Post by Guyofdoom42 on 2014-12-29
So, I want to install a double-wide GPU, but I only have 1 PCIe slot.

Here's the layout of my Motherboard.

|-------------------------------------------Front of computer                                           [======================] PCIe slot -| Back
|------------------------------------------------------------------------------------------|                                                                          Something or other [====]                   -|
|---------------------------------------------------------------------------------                                                                               [=================] PCI slot  |
|----------------------------------------------------------------------------------------------[=================]               -|
|------------------------------------------------------------------------------------------------------------------------------------|
|------------------------------------------------------------------------------------------------------------------------------------|
------------------------------------------------------------------------------------------------------------------------------------ Bottom

The motherboard is on the left side of the computer.

I can't afford to upgrade the Motherboard, or buy a new case.

Please help!

---

### Post by QIII on 2014-12-29
Hello!

You'll simply need to install it in the PCIe slot assuming you have physical clearance.  If you don't have the expansion slot "knock out" to fit there, you may simply not be able to do it unless you find a flexible riser and move it to where you have two adjacent expansion slots.

The problem with that, however, would be that without the PCB plugged into the slot the GPU would be hanging unsupported by anything but the screws at the back -- which would almost certainly damage the GPU.

---

### Post by overdrank on 2014-12-29
You want to post the motherboard model and look at additional power requirements for the new card.

---

### Post by QIII on 2014-12-29
A snapshot of the rear inside of the case would also be helpful.  Is there an expansion slot in the case above the bottom of the motherboard (remember that your board is inverted so its bottom is at the top of the case if this is a conventional mobo).

If the mobo is some sort of odd proprietary format, you may be stuck.

---

### Post by pqwoerituytrueiwoq on 2014-12-29
i think i know what your issue is
you only have 1 PCI-e slot, buy you think a double wide card uses 2 of those, well it only uses one and blocks access to the next slot (unless you use a cable to relocate the plug)
a double wide card uses 1 plug on the motherboard and 2 slots on the case
as long as you have power for the GPU and room for airflow it will work just fine

---

### Post by Guyofdoom42 on 2015-01-06
Nononono, It looks like if I put a Dual-Width card in there, half of it would be above the top slot, so It wouldn't fit without me cutting my case up.

---

