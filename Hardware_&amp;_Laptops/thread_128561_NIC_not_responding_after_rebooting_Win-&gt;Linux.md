---
title: "NIC not responding after rebooting Win-&gt;Linux"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by el3ktro on 2006-02-11
I have an nForce4-based mainboard from ASRock (Socket 754). I dual-boot with WinXP & Ubuntu, and I use the forcedeth driver. When turning on my computer and boot into WinXP, everythings fine. When I reboot into Ubuntu then the NIC is not functional at all - eben modprobe -r forcedeth doesn't help. When I turn on the computer and boot into Ubuntu straight away everything's fine, also when I reboot into XP. What the heck is WinXP doing with my NIC? Has anybody experienced the same?

Tom

---

### Post by BenTyreman on 2006-02-11
I had this problem on my laptop. I eventually tracked it down to whenever I hibernated XP and booted into linux, my network card refused to work. I reckon that the driver for XP was somehow setting the network card into a state that the linux driver was unable to retrieve it from. Perhaps this is a similar thing?

---

