---
title: "temperature before/after hibernate (acpi)"
date: 2006-01-16
forum: Hardware &amp; Laptops
---

### Post by emaru on 2006-01-16
Hi all,

I have a Breezy installed on a BenQ Joybook 7000 laptop, works quite nice, except for strange readings from the acpi temperature sensors. The CPU Frequency Scaling Monitor (and similar applets) detects two sensors, THZV and THZN. I'm guessing the first one is the cpu temperature and the second the motherboard because the first is always 8-10 C warmer. After a cold boot the cpu temp seems quite high, between 61 and 65 C, even when there's hardly any activity and the cpu is scaled down to minimum (600MHz on a 1.6 GHz Dothan processor - btw no proper centrino speedstepping yet, only two steps provided by acpi, but I've read about kernel patches to fix that, that'll be my next project). Is that really high? fan does kick in occasionally, but I'm not sure if it's really too often, in any case it does so without the speedstep/cpu activity going up. The really strange thing is that, after hibernate, the temperature drops dramatically and hovers around 52-54, and stays there. Do you think it really did drop or is it most likely an issue with the acpi sensors readings? Anybody else have this? Is 65 C really way too high for an idle machine? Does it make any sense to always hibernate and wakeup (after a reboot), just to be on the safe side? Would rebuilding the kernel with real centrino-speedstepping help, or does that not affect hibernation/temperature sensors at all?
Thanks already!

---

