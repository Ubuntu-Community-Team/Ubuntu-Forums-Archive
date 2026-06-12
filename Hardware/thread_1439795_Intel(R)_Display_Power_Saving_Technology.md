---
title: "Intel(R) Display Power Saving Technology"
date: 2010-03-26
forum: Hardware
---

### Post by ddiddo on 2010-03-26
Actually I am not quite sure if this feature is supported but I have some problems and if it is supported I need a way to disable it. There is not an option in the BIOS to turn it off.

The video controller is Intel GMA 4500MHD (in the Mobile Intel GM45 Express Chipset).

The output from lshw:

*-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:29 memory:f6c00000-f6ffffff memory:e0000000-efffffff(prefetchable) ioport:efe8(size=8)


and from lspci:

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

### Post by jmate24 on 2010-03-26
your asking how to disable the power saving of your graphics controller?

if you are then you just need to go to the System>Preferences>Screensaver Application

then click the Power Management button at the bottom of the window and then adjust the settings to what you need

---

### Post by ddiddo on 2010-03-27
> **jmate24 said:**
> your asking how to disable the power saving of your graphics controller?

if you are then you just need to go to the System>Preferences>Screensaver Application

then click the Power Management button at the bottom of the window and then adjust the settings to what you need
I want to disable the "Intel Display Power Saving Technology" feature of the video controller. I don't see an option in the** "**Power Management" dialog that would correspond to this feature. What option do you have in mind?

---

