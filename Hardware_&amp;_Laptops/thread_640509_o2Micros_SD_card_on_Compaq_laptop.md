---
title: "o2Micros SD card on Compaq laptop"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by mbsnr on 2007-12-14
Hi

I have a Compaq nc8000 with this internal SD card reader reported by lspci (SD reader works on the Windows XP boot)

02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller

I have in /etc/modules
tifm_sd
tifm_7xx1
tifm_core

and dmesg | grep cardbus gives
[   16.268801] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[   16.268820] PCI: Bus 5, cardbus bridge: 0000:02:06.1
[   16.268839] PCI: Bus 9, cardbus bridge: 0000:02:06.3

But I can't see my SD card in the reader.... Any ideas what I can try next?

---

### Post by mbsnr on 2007-12-17
PS Running Gusty... 

Can anyone help here?

---

### Post by cyrusrayne on 2007-12-18
Very interesting issue.  I've got a similar reader in my laptop but haven't encountered the problem in Gutsy as yet.  Will take a look and see if I can get back to you.

---

### Post by mbsnr on 2007-12-18
Great thanks!

Seems that tifm_sd (Texas Instruments Firmware Module), tifm_7xx1 and  tifm_core in /etc/modules work only on Texas Instruments card readers. So I need something for a O2 Micro reader. However searching the internet it seems that there is no dedicated module for O2 Micros readers ....All I find is posts asking but no solution!

---

### Post by cyrusrayne on 2007-12-23
My reader shows as follows in my Device Manager under the preferences menu:

info.linux.driver:sdhci (for MMC/SD)
and driver shows as yenta_cardbus for my cardbus.

It doesn't return specifics for the device for Memory Stick/XD but all comes out to being under an integrated controller from O2 Micro.  I will note though that it does not work 100% of the time, though the driver info for the MMC/SD and cardbus are the only driver info I could glean from my configuration.

---

### Post by mbsnr on 2007-12-27
Thanks for the reply.

TBH I've jacked in Ubuntu and Linux yet again. I'll come back to it after a while no doubt as I have before.... Google Earth was the show stopper - doesn't work with my laptop ATI graphics card and I'm really getting fed up with constantly having to go to the forums to try and get things working which *should* just work from the outset.

Apparently Ubuntu "Just Works" - Not my experience on the 3 or so laptops I've tried. There's always something that doesn't just work. (For the record I have a Ubuntu server running Openfire and it does work. But I think that's more to do with the fact that I'm not trying to run desktop effects or other apps on it).

---

