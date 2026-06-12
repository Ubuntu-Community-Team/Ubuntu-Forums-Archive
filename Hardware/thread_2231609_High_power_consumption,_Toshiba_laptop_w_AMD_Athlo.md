---
title: "High power consumption, Toshiba laptop w/ AMD Athlon X2 Dual-Core QL-64"
date: 2014-06-26
forum: Hardware
---

### Post by weatherman2 on 2014-06-26
Older Toshiba L305D laptop with Athlon X2 Dual-Core QL-64 CPU and Radeon video card.  Came with Vista.  I have installed the latest BIOS available from Toshiba.

I have a power consumption meter.

At idle, with Vista, laptop consumes about 28 watts.

At idle, with Ubuntu 14.04, laptop consumes about 38 watts.  (This when the CPU is under almost no load.)  Same thing under 12.04.

I played with the Radeon driver - changed the power save settings.  Set it to the lowest power mode, and power drops almost 1 watt.

Also tried setting Grub boot parameter of "acpi_osi=Linux" and that also dropped power consumption about 1 watt. But clearly I'm way off from what I get under Vista.  I assume something is misconfigured, wrong driver, etc.

Any suggestions for other things I can try?  Higher power consumption means more heat, fan on more often, and in a laptop greatly reduced battery life not to mention excess use of electricity even if not that much.

I can leave Vista on this laptop and get rid of it, would prefer not to.  I don't have these issues with Intel-based laptops.

---

