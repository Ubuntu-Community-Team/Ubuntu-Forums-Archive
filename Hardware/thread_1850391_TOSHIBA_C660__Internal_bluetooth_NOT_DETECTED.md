---
title: "TOSHIBA C660 : Internal bluetooth NOT DETECTED"
date: 2011-09-26
forum: Hardware
---

### Post by lordbux on 2011-09-26
Hai friends 

I am using a** TOSHIBA C660 **
**Ubuntu 10.04 Lucid Lynx** 

My problem is that the internal bluetooth adapter is not being recognized by my system. 
**at System>Preferences>Bluetooth  i have the message**
> Your Computer doesnot have any bluetooth adapters plugged in.


Please help with this: MY  **toshset command gives output **
```
required kernel toshiba support not enabled.

```

My LSPCI Output: 
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

Please help me with this. 
Thanks in advance:)

---

### Post by maul9999 on 2011-09-26
> **lordbux said:**
> Hai friends 

I am using a** TOSHIBA C660 **
**Ubuntu 10.04 Lucid Lynx** 

My problem is that the internal bluetooth adapter is not being recognized by my system. 
**at System>Preferences>Bluetooth  i have the message**


Please help with this: MY  **toshset command gives output **
```
required kernel toshiba support not enabled.

```My LSPCI Output: 
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
06:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```Please help me with this. 
Thanks in advance:)

Can you tell me what is your Bluetooth model?

---

### Post by lordbux on 2011-09-26
its inbuilt, TOSHIBA C660. 
its not external

---

### Post by lordbux on 2011-09-26
> **lordbux said:**
> hai friends 

i am using a** toshiba c660 **
**ubuntu 10.04 lucid lynx** 

my problem is that the internal bluetooth adapter is not being recognized by my system. 
**at system>preferences>bluetooth  i have the message**


please help with this: My  **toshset command gives output **
```
required kernel toshiba support not enabled.

```

my lspci output: 
```

00:00.0 host bridge: Intel corporation core processor dram controller (rev 02)
00:02.0 vga compatible controller: Intel corporation core processor integrated graphics controller (rev 02)
00:16.0 communication controller: Intel corporation 5 series/3400 series chipset heci controller (rev 06)
00:1a.0 usb controller: Intel corporation 5 series/3400 series chipset usb2 enhanced host controller (rev 05)
00:1b.0 audio device: Intel corporation 5 series/3400 series chipset high definition audio (rev 05)
00:1c.0 pci bridge: Intel corporation 5 series/3400 series chipset pci express root port 1 (rev 05)
00:1c.1 pci bridge: Intel corporation 5 series/3400 series chipset pci express root port 2 (rev 05)
00:1d.0 usb controller: Intel corporation 5 series/3400 series chipset usb2 enhanced host controller (rev 05)
00:1e.0 pci bridge: Intel corporation 82801 mobile pci bridge (rev a5)
00:1f.0 isa bridge: Intel corporation mobile 5 series chipset lpc interface controller (rev 05)
00:1f.2 sata controller: Intel corporation 5 series/3400 series chipset 4 port sata ahci controller (rev 05)
00:1f.3 smbus: Intel corporation 5 series/3400 series chipset smbus controller (rev 05)
00:1f.6 signal processing controller: Intel corporation 5 series/3400 series chipset thermal subsystem (rev 05)
01:00.0 ethernet controller: Realtek semiconductor co., ltd. Rtl8101e/rtl8102e pci express fast ethernet controller (rev 05)
06:00.0 network controller: Broadcom corporation device 4727 (rev 01)
ff:00.0 host bridge: Intel corporation core processor quickpath architecture generic non-core registers (rev 05)
ff:00.1 host bridge: Intel corporation core processor quickpath architecture system address decoder (rev 05)
ff:02.0 host bridge: Intel corporation core processor qpi link 0 (rev 05)
ff:02.1 host bridge: Intel corporation core processor qpi physical 0 (rev 05)
ff:02.2 host bridge: Intel corporation core processor reserved (rev 05)
ff:02.3 host bridge: Intel corporation core processor reserved (rev 05)

```

please help me with this. 
Thanks in advance:)

bump

---

