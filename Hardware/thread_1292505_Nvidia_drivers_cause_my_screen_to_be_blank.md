---
title: "Nvidia drivers cause my screen to be blank?"
date: 2009-10-15
forum: Hardware
---

### Post by HngGstr on 2009-10-15
So I go to my Hardware Drivers, and I activate "NVIDIA accelerated graphics driver (version 180)." After I restart and try to boot into Ubuntu, my screen goes black. What gives?

If it makes a difference, I'm running 9.04

---

### Post by miltonhork on 2009-10-16
Hi
    Start the laptop in Safe Mode first, this will stop the faulty driver being loaded and cause it to use the Windows Plug & Play driver. While in safe mode uninstall the faulty driver. Restart your laptop in normal and you should have a display as it now defaults to the Plug & Play driver as the WHQL driver is not there, now install your driver, restart and your hot to trot.

---

