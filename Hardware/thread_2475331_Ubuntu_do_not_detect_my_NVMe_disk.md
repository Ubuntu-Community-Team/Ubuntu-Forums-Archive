---
title: "Ubuntu do not detect my NVMe disk"
date: 2022-05-23
forum: Hardware
---

### Post by frm77000 on 2022-05-23
Hi dear Ubuntu community

I'm asking your help to understand why my ubuntu do not detect my disk
I recently added a PCIe card which seem to be detect correctly

> 05:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 04) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 255, IOMMU group 12
    Bus: primary=05, secondary=06, subordinate=06, sec-latency=32
    I/O behind bridge: [disabled]
    Memory behind bridge: [disabled]
    Prefetchable memory behind bridge: [disabled]
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Power Management version 3
    Capabilities: [80] Express PCI-Express to PCI/PCI-X Bridge, MSI 00
    Capabilities: [c0] Subsystem: ASUSTeK Computer Inc. ASM1083/1085 PCIe to PCI Bridge
    Capabilities: [100] Virtual Channel

> sudo dmesg | grep 05:00
[    0.325074] pci 0000:05:00.0: [1b21:1080] type 01 class 0x060400
[    0.325215] pci 0000:05:00.0: supports D1 D2
[    0.325216] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.325456] pci 0000:05:00.0: PCI bridge to [bus 06]
[    0.436949] pci 0000:05:00.0: PCI bridge to [bus 06]
[    0.437684] pci 0000:05:00.0: Disabling ASPM L0s/L1
[    0.437897] pci 0000:05:00.0: Adding to iommu group 12



But the problem is the nvme disk is not detect.
What is strange is that my disk is perfectly detected when I boot using a live usb.
I double check a lot of parameters but nothing change.
my version is 22.04 but was the same problem with 21.10 before upgrade.
I also test a lot of different kernel.

Thanks in advance for your help

Franck

---

### Post by rsteinmetz70112 on 2022-05-23
What is the nvme disk connected to?

---

### Post by frm77000 on 2022-05-23
Hi [URL="https://ubuntuforums.org/member.php?u=252572"][COLOR=#000000]rsteinmetz

The disk is a Western Digital ([/COLOR][/URL]**WD Gold 1,92 To PCIe Gen. 3 - Wds192t1d0d )**

Thanks

---

### Post by frm77000 on 2022-05-27
Hi Community
not any idea ?

Thank you all

---

### Post by Yellow Pasque on 2022-05-27
You should carefully check your motherboard's manual for limitations on which connectors can be used at the same time. Sometimes, you can only use certain combinations of SATA, PCIe, and M.2 slots due to PCIe lane limitations.

---

### Post by frm77000 on 2022-05-27
Thank you Yellow Pasque
What is strange it that when I boot from a live usb my nvme is well detected..the same if I boot on my windows partition..

So it let me think that is not an hardware limitation.

I tried to verify which module is started when bootng with live usb but it seems that I have the same module loaded.
What software/drivers/module is need to have a nvme disk detected :D :D

Regards

---

