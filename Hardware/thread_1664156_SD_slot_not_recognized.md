---
title: "SD slot not recognized"
date: 2011-01-10
forum: Hardware
---

### Post by CompuTom on 2011-01-10
I have a Fujitsu Lifebook P5020 which runs Ubuntu 9.4 like a dream except it does not recognize the SD card slot. Is there any hope for me to use this SD card slot? The lifebook will not run Ubuntu 10. Thanks for your help.

---

### Post by ajgreeny on 2011-01-10
Is that for any SD card or just SDHC cards.  Some card readers will only see the old SDs and totally ignore SDHC cards, so I wonder if that is the case with your slot.

---

### Post by CompuTom on 2011-01-10
the SD slot is in an older notebook and only reads standard SD up to 2 GIG. SDHC are notsupported, But I have the SD cards I used in this drive under Windows so I know they are compatible with the hardware. I think it is a driver issue for Ubuntu 9.10, the only other trouble I have is not being able to watch DVD movies like in Windows. Missing codecs. Can anyone help?

---

### Post by CompuTom on 2011-01-10
For what its worth, the WiFi works better under Ubuntu than it ever did under Windows! I will miss this notebook when it finally goes obsolete, cause it will never fail. It is built rock solid, with a magnesium-alloy chassis and quality components. Ubuntu 9.1 support ends in a few months and like I said before this notebook will not run Ubuntu 10. My digital camera uses SD cards and it would be nice to just plug them into the notebook.

---

### Post by efflandt on 2011-01-10
Did you install **ubuntu-restricted-extras**, or at least **flashplugin-installer** which is included in the restricted-extras along with java and codecs.  Most internet video is flash (except Netflix which uses Silverlight and does not currently work in Linux).

Also see the description of ubuntu-restricted-extras about what else you would need to do to view DVDs.

As far as the card reader, what does **sudo lspci -v** show about that device?  And does **dmesg** show anything about it, especially when you insert SD?  Often ones built into laptops are a different type of block device (not usb mass storage) that you cannot boot from even if it does automount.  But a USB memory card reader should work if you cannot get your built-in reader to work.

The one in my Toshiba laptop (from 2006) shows 2 devices in lspci:

Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
using module tifm_7xx1

SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
using module sdhci-pci

```
efflandt@efflandt-laptop:~$ **dmesg | grep sdhci**
[   31.273788] sdhci: Secure Digital Host Controller Interface driver
[   31.273791] sdhci: Copyright(c) Pierre Ossman
[   31.275412] sdhci-pci 0000:07:06.3: SDHCI controller found [104c:803c] (rev 0)
[   31.275441] sdhci-pci 0000:07:06.3: PCI INT A -> GSI 18 (level, low) -> IRQ 18

and after inserting SD the tail end of dmesg shows:
[  940.780160] tifm_core: MMC/SD card detected in socket 0:1
[  941.069050] mmc1: new SD card at address eded
[  941.098801] mmcblk0: mmc1:eded S008B 6.48 MiB 
[  941.098901]  mmcblk0: p1
```Which means that the SD is /dev/mmcblk0 and the partition on it is /dev/mmcblk0p1

---

