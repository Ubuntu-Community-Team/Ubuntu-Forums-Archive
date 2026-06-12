---
title: "dell inspiron b130 graphics driver"
date: 2009-11-05
forum: Hardware
---

### Post by petey1993 on 2009-11-05
i have the i910gm chipset(correct me if i'm wrong)
i have the driver from [here]("http://http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=8203&ProdId=1862&lang=eng")
and i can't seem to install it...
or find out how...
help please?

here is the list that has to do with graphics from lspci -v
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Dell Device 01c9
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at eff8 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Dell Device 01c9
    Flags: bus master, fast devsel, latency 0
    Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>sorry if it's already installed lol
i'm just kinda new to linux still

---

