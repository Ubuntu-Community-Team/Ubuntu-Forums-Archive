---
title: "Missing Intel driver?"
date: 2011-07-24
forum: Hardware
---

### Post by MG&amp;TL on 2011-07-24
I have an Ubuntu 11.04 Sony VAIO laptop with built-in Intel graphics. However, 'Additional drivers' does not have anything there. Am I meant to install anything?

'lspci' returns 


```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller
03:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller
03:00.4 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] (rev 11)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

Can anyone help me on this one? Thanks guys. Do I need to go on the web to find them?

---

### Post by Mcjohnnson on 2011-07-24
No, you do not need an additional driver. Open a terminal and tell us what
```
lsmod | grep 915
```
is giving back.

---

### Post by MG&amp;TL on 2011-07-24
Can't access the laptop in question at the moment, will do that as soon as I can. Why doesn't it need a driver? Where does the 'puter get the files from then? Thanks for reply!

---

### Post by MG&amp;TL on 2011-07-24
```
i915                  450969  8 
drm_kms_helper         40745  1 i915
drm                   184133  4 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915

```

Here it is!

---

### Post by coffeecat on 2011-07-24
> **MG&TL said:**
> Why doesn't it need a driver?

Of course it needs a driver, but the driver is included in a default install. The Intel video driver is open-source with Intel helping in the development. There is no separate proprietary blob as with nvidia or ATI which is why Additional Drivers is not prompting you to install anything.

Is video working OK on that laptop? If so, you needn't do anything.

---

### Post by MG&amp;TL on 2011-07-24
Video is working fine, I just assumed that Intel would be as touchy as other companies about their licensing. Assumed that my graphics card was running in limited mode or something...thanks McJohnson and CoffeCat.

---

### Post by coffeecat on 2011-07-24
> **MG&TL said:**
> I just assumed that Intel would be as touchy as other companies about their licensing.

An understandable assumption, but in fact Intel does co-operate. Kudos to both Intel and ATI/AMD for working with the open-source community to produce open source video drivers for Linux for their respective products.

Glad to hear you video is working fine. Good luck!

---

