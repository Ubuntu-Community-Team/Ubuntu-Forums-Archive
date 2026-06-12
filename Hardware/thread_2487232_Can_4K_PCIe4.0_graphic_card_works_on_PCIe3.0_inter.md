---
title: "Can 4K PCIe4.0 graphic card works on PCIe3.0 interface?"
date: 2023-05-28
forum: Hardware
---

### Post by satimis on 2023-05-28
**[COLOR="#FF0000"]Can 4K PCIe4.0 graphic card works on PCIe3.0 interface?[/COLOR]**

Hi all,

Hardware:-
CPU AMD Ryzen 5 3400G with Radeon Vega Graphics
Motherboard  ASUS PRIME X570-P (PCIe 3.0 interface)
32G RAM onboard
Display: Dell 32" 4K monitor U3219Q
(Graphic comes from AMD CPU without graphic card installed.)

OS Linux Ubuntu 22.04 desktop

Recently at booting following warning:```

The current input time is not supported by the monitor display.  Please change your input timing to 3840x2160, 60Hz or any other monitor
.....

```

is always handing a while on monitor and then popup to login page, Boot Menu not started,  It didn't happen in the past.  Setting of the Dell monitor is exactly 3840x2160, 60Hz 

I hesitate whether the problem comes from the graphic because without a 4K graphic card.  

I'm prepared to purchase a a 4K graphic card, PCIe 4.0 interface, to check whether the problem can be solved.  If NOT then I'll build a new AMD Ryzen 9 PC, using the new 4K graphic card.

Please advise whether 4K PCIe 4.0 graphic card works on PCIe 3.0 interface?  My old motherboard only provide PCIe 3.0 interface.

Thanks in advance.

**[COLOR="#FF0000"]Edit[/COLOR]**
Made following test:-

Change the monitor to a 24" 2560x1440 resolution, then the problem gone.  Grub menu starts at boot

Possibly "CPU AMD Ryzen 5 3400G" can't support 4K graphic

Regards

---

### Post by Autodave on 2023-05-28
Yes.  However, it will be running at PCIe 3 speed.

---

### Post by satimis on 2023-05-28
> **Autodave said:**
> Yes.  However, it will be running at PCIe 3 speed.
Thanks for your advice.

It is only temporary.   I can still use this PCIe 4.0 graphic card in the new PC.

Regards

---

