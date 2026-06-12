---
title: "Ubuntu doesn't recognize my AMD graphics"
date: 2012-12-14
forum: Hardware
---

### Post by lazarojhr16 on 2012-12-14
I'm using Ubuntu 12.10. My laptop has an AMD 3100 graphics. When I go to software sources, it has nothing. What can I do so that Ubuntu recognizes my graphics card. 

when I do lspci on the terminal, I can see my graphics card.
Here is the output:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS780MC [Mobility Radeon HD 3100 Graphics]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

```

What can I do? Thanks for the help.

---

### Post by TOMBSTONEV2 on 2012-12-14
Do you have additional drivers activated for your graphics card? (System settings>Hardware Additional Drivers)

---

### Post by QIII on 2012-12-14
AMD/ATI has moved support for the driver for all HD 1000 to HD 4000 series cards to a legacy branch.  The drivers will not work with X Server 1.13, which is used by Ubuntu 12.10.  Thus, you will not find a driver offered by Quantal for your card.

The most recent version of Ubuntu for which a proprietary driver will support your card is 12.04.

You have three options, in the order I would recommend them:

1.  Continue to use the open source Radeon driver (the default) and install Jupiter to control power consumption (and the heat associated) and to extend battery life.  The Radeon driver will fulfill the needs of the vast majority of users.

2.  Downgrade to 12.04 and use the legacy driver, since it will work.

3.  Break 12.10 by following several sites' instructions for downgrading X Server to 1.12 and using the proprietary legacy driver.

I strongly recommend against the last, although that suggestion will probably be presented in this thread.  It effectively breaks and hobbles your OS and the consequences of doing so may be catastrophic at some point in the future if you upgrade you version of Ubuntu to one that uses an even newer version of X Server.

---

### Post by Bucky Ball on 2012-12-14
Not sure what you would expect to find in Software Sources related to this.

If you're not happy with the current driver you could, as suggested, install 12.04 LTS. Supported til 2017 rather than for the next 18 months anyhow.

---

### Post by lazarojhr16 on 2012-12-14
> **QIII said:**
> AMD/ATI has moved support for the driver for all HD 1000 to HD 4000 series cards to a legacy branch.  The drivers will not work with X Server 1.13, which is used by Ubuntu 12.10.  Thus, you will not find a driver offered by Quantal for your card.

The most recent version of Ubuntu for which a proprietary driver will support your card is 12.04.

You have three options, in the order I would recommend them:

1.  Continue to use the open source Radeon driver (the default) and install Jupiter to control power consumption (and the heat associated) and to extend battery life.  The Radeon driver will fulfill the needs of the vast majority of users.

2.  Downgrade to 12.04 and use the legacy driver, since it will work.

3.  Break 12.10 by following several sites' instructions for downgrading X Server to 1.12 and using the proprietary legacy driver.

I strongly recommend against the last, although that suggestion will probably be presented in this thread.  It effectively breaks and hobbles your OS and the consequences of doing so may be catastrophic at some point in the future if you upgrade you version of Ubuntu to one that uses an even newer version of X Server.

Ok thank you. I didn't know AMD did that. Will probably go with your first suggestion. thank you again.

---

