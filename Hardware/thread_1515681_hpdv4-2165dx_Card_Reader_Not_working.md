---
title: "hpdv4-2165dx Card Reader Not working"
date: 2010-06-22
forum: Hardware
---

### Post by fr3ak.m3 on 2010-06-22
I have a hpdv4-2165dx and the card reader isn't working. It is working fine with my OEM Windows and also with splashtop... If it works with splashtop(a linux variant) which means they do have drivers(kernel modules) for the device. I also tried writing a krenel module for it but all my attempts failed. I couldn't read the higher bytes of the configuration space(40th byte and higher) under Windows system...

Here is my lspci -k -nn
```
03:00.1 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5288] (rev 01)
    Kernel modules: windrvr6
03:00.2 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. Device [10ec:5288] (rev 01)
    Kernel driver in use: sdhci-pci
    Kernel modules: windrvr6, sdhci-pci

```
The device 03.00.01 is my card reader.... And it is not recognized under Ubuntu.....

My dmesg after I modprobe sdhci-pci
```
[ 3162.829268] sdhci: Secure Digital Host Controller Interface driver
[ 3162.829274] sdhci: Copyright(c) Pierre Ossman
[ 3162.833161] sdhci-pci 0000:03:00.2: SDHCI controller found [10ec:5288] (rev 1)
[ 3162.833241] sdhci-pci 0000:03:00.2: PCI INT C -> GSI 16 (level, low) -> IRQ 16
[ 3162.833713] sdhci-pci 0000:03:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
[ 3162.833748] sdhci-pci 0000:03:00.2: setting latency timer to 64
[ 3162.834302] Registered led device: mmc0::
[ 3162.834378] mmc0: SDHCI controller on PCI [0000:03:00.2] using DMA

```
Only the led device of the controller is working and the kernel module isn't being loaded for 03.00.01 just for 03.00.02

This is not a USB device so lsusb won't be helpful... Hope I get positive response for the community. I would also like to know if there is any tool that can dump PCI Configuration Registers under 64 bit windows 7?

---

