---
title: "SmartCard reader o2 micro 1394 not working on DELL e5420"
date: 2014-04-11
forum: Hardware
---

### Post by Tanel_Tammik on 2014-04-11
Hello,

can anyone tell me, how to fix this problem?

```
09:00.0 FireWire (IEEE 1394): O2 Micro, Inc. 1394 OHCI Compliant Host Controller (rev 05)
09:00.1 SD Host controller: O2 Micro, Inc. Integrated MMC/SD controller (rev 05)
```

           ```
*-firewire
                description: FireWire (IEEE 1394)
                product: 1394 OHCI Compliant Host Controller
                vendor: O2 Micro, Inc.
                physical id: 0
                bus info: pci@0000:09:00.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:17 memory:e3b30000-e3b30fff
           *-generic
                description: SD Host controller
                product: Integrated MMC/SD controller
                vendor: O2 Micro, Inc.
                physical id: 0.1
                bus info: pci@0000:09:00.1
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:18 memory:e3b20000-e3b201ff
```



perhaps push me into the right direction, how to address this problem. According to ubuntu, this device is supported.

---

