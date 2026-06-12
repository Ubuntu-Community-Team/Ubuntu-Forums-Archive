---
title: "SD Card reader low performance"
date: 2013-10-23
forum: Hardware
---

### Post by HCPy8k6 on 2013-10-23
I'm using HP Folio 9470m which has built-in JMicron's (probably JMB38x) sd card reader (details below). Reader works fine with Sandisk Extreme 32GB 80/60MBps, however performance is a bit disappointing. Under Windows 7 it reaches easily declared read/write speeds, while under XUbuntu 13.10 it doesn't perform that good, 20/7 MBps is maximum I get. Performance is critical to me because this sd card is used for hosting XUbuntu OS. I've noticed one problem in dmesg:

konrad@apollo:~$ dmesg | grep mmc
[    2.518975] mmc0: no vqmmc regulator found
[    2.518979] mmc0: no vmmc regulator found
[    2.519097] mmc0: SDHCI controller on PCI [0000:02:00.0] using DMA
[    2.763278] mmc0: new SDHC card at address e624
[    2.765700] mmcblk0: mmc0:e624 SU32G 29.7 GiB 
[    2.766606]  mmcblk0: p1

Does it mean that the card is unable to switch to fast 1.8v mode?

Details about reader:

konrad@apollo:~$ sudo ls -vnn

02:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2392] (rev 30)
    Subsystem: Hewlett-Packard Company Device [103c:18df]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at d0503000 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at bf200000 [disabled] [size=64K]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-
    Kernel driver in use: sdhci-pci

02:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2391] (rev 30) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device [103c:18df]
    Flags: fast devsel, IRQ 18
    Memory at d0502000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a4] Power Management version 3
    Capabilities: [80] Express Endpoint, MSI 00
    Capabilities: [94] MSI: Enable- Count=1/1 Maskable- 64bit-


Any help is appreciated.

---

