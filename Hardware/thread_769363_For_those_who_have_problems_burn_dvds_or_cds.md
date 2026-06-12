---
title: "For those who have problems burn dvds or cds"
date: 2008-04-26
forum: Hardware
---

### Post by oberonking on 2008-04-26
Hi.... I was looking for a solution for this issue, and finally came.

The solution for me was compile the kernel adding the support for Ide of my chipset (Nforce 430 == amd74xx) and libata, 	
That allowed me to again turn off dma, that's the only way that I have to burn on my device (Asus drw-1608p2)... the burn takes twice now, but burn every time....

Mi tip for all of you has..... search for your modules to turn back /dev/hdXX stuff.... and try to burn with dma active if that fails, then turn it off.

That works for me, I'm not able to burn anything since Feisty if active DMA for burner device.

That's all for now... ask if you want ;)

---

