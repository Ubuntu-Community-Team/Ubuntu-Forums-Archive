---
title: "Wireless takes a long time to start."
date: 2008-10-22
forum: Hardware
---

### Post by OlaNordmann on 2008-10-22
Hey ubuntufolks.

I'm having a bit of difficulties with my wireless adapter that I can't figure out. I was hoping I could get some help, since everything else works wonderful..

The Problem:
My wireless works. But for some reason it takes a long time (often 5-10 minutes) to start and become active.

 Short summary: 
It's an ASUS eeePC 901, running Ubuntu 8.04 with custom kernel from Array.org, and Adamm's acpi event script (FN function buttons).
**$ lspci** prints "*01:00.0 Network controller: RaLink Unknown devaice 0781*" and **$ sudo iwlist ra0 scan** (ra0 is the wirless interface) gives no results before it becomes active.


When turning on wireless, dmesg prints this:
```

[20422.578289] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 unloaded
[20425.781820] pciehp: HPC vendor_id 8086 device_id 27d0 ss_vid 0 ss_did 0
[20425.781962] Load service driver hpdriver on pcie device 0000:00:1c.0:pcie02
[20425.781994] pciehp: HPC vendor_id 8086 device_id 27d2 ss_vid 0 ss_did 0
[20425.782198] Load service driver hpdriver on pcie device 0000:00:1c.1:pcie02
[20425.782230] pciehp: HPC vendor_id 8086 device_id 27d4 ss_vid 0 ss_did 0
[20425.782303] Load service driver hpdriver on pcie device 0000:00:1c.2:pcie02
[20425.782332] pciehp: HPC vendor_id 8086 device_id 27d6 ss_vid 0 ss_did 0
[20425.782397] Load service driver hpdriver on pcie device 0000:00:1c.3:pcie02
[20425.782412] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[20425.797235] pciehp: Card present on Slot(0001_0000)
[20426.848585] program_fw_provided_values: Could not get hotplug parameters
[20426.934796] PCI: Enabling device 0000:01:00.0 (0000 -> 0002)
[20426.934818] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[20426.935275] 
[20426.935278] 
[20426.935280] === pAd = f8f83000, size = 580788 ===
[20426.935283] 
[20426.935288] <-- RTMPAllocAdapterBlock, Status=0
[20426.935329] PCI: Setting latency timer of device 0000:01:00.0 to 64
[20426.982658] RX DESC ef6f6000  size = 2048
[20426.983235] <-- RTMPAllocTxRxRingMemory, Status=0
[20426.986961] 1. Phy Mode = 0
[20426.986973] 2. Phy Mode = 0
[20427.008245] RTMPSetPhyMode: channel is out of range, use first channel=1 
[20427.014697] 3. Phy Mode = 0
[20427.014716] MCS Set = 00 00 00 00 00
[20427.018538] <==== RTMPInitialize, Status=0
[20427.018621] 0x1300 = 00073200
```


Then, suddently after about 5 minutes (often it won't start at all):
```
[20438.148830] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 197
[20439.477562] ADDRCONF(NETDEV_CHANGE): ra0: link becomes ready
[20439.612317] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 197
[20447.126488] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 197

```

The problem occurs without hotplugging as well.. when booting up with wifi enabled, it still takes a long time.

I'm actually very dependent on wifi because I use the laptop at school.

---

