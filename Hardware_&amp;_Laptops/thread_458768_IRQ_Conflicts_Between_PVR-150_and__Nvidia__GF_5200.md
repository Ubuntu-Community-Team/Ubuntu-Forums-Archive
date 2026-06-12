---
title: "IRQ Conflicts Between PVR-150 and  Nvidia  GF 5200"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by Darkdelusions on 2007-05-30
When I start loading ubuntu after adding 2 pvr-150 in my box I am getting the error message: PCI: Failed to allocate mem resource #1:10000000@e0000000 for 0000:01:00.0 which happens to be my nvidia gf5200. This is creating a problem in X windows it Make Xwindows look like a scrambled paper view channel (White less and distorted video) I have scoured google and have been unable to find anything. 

This is also happening with i just have 1 pvr 150 in the box. If i take PVR's out they load fine. 




Also I am getting the error 

[   28.910933] Setting up standard PCI resources
[   28.965010] PCI: Cannot allocate resource region 1 of device 0000:01:00.0
[   28.971831] PCI: Failed to allocate mem resource #1:10000000@e0000000 for 0000:01:00.0


** Note this also happens when I have 1 PVR-150 in the box as well 

However I just did a LSPCI -v 

PVR-150  IRQ 11
PVR-150  IRQ 5
NV GF 5200 IRQ 10

AMD Athlon FX 51
MSI K8T Master
1 gig of ram
2 x PVR150

---

### Post by Darkdelusions on 2007-05-30
Double post

---

### Post by Darkdelusions on 2007-05-30
Anyone have any ideas?

---

