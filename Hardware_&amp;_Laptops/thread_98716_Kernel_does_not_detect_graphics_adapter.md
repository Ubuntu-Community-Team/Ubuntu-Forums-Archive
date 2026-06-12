---
title: "Kernel does not detect graphics adapter"
date: 2005-12-04
forum: Hardware &amp; Laptops
---

### Post by Timokl on 2005-12-04
It seems I have found the reason, why Ubuntu Breezy does not install the fglrx drivers for my ATI Mobility Radeon X600 -- obviously it does not recognise the card. :( After entering *lspci* into a terminal, I get the following:

```
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 01)
0000:00:02.0 PCI bridge: ATI Technologies Inc: Unknown device 5a34 
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:07.0 PCI bridge: ATI Technologies Inc: Unknown device 5a39

```

I finally managed to configure my xorg.conf to make X11 use the ati driver, so I could switch to 1200x800 screen resolution. However, I am not sure, whether this is the best driver for 2D stuff and (possibly) watching movies. 

What can you advise me to do. Keep this driver (never change a running system?) or try to install the fglrx driver?

---

### Post by newuser111 on 2005-12-04
i recommend the fglrx driver and the restricted modules for your kernel

---

