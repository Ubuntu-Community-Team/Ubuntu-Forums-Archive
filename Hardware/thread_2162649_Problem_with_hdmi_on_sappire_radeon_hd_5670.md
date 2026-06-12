---
title: "Problem with hdmi on sappire radeon hd 5670"
date: 2013-07-15
forum: Hardware
---

### Post by eugeds on 2013-07-15
Hello

I have a problem with my graphic card radeon hd 5670. When connect a monitor with hdmi cable the monitor stay black and show the no signal message. 
If i connect another monitor with DVi connector this show a normal ubuntu desktop, after this, if connect the second monitor with hdmi, all monitors show the no signal message and stays black. 

how can I solve this problem?

the lspci result is:

```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Redwood XT [Radeon HD 5670/5690/5730]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series]
02:00.0 Ethernet controller: Qualcomm Atheros AR8131 Gigabit Ethernet (rev c0)


```

thanx

---

### Post by eugeds on 2013-07-15
I forgot, 
I use ubuntu 13.04

thanx

---

### Post by eugeds on 2013-07-16
help me please

---

### Post by jp734 on 2013-07-16
okay. few questions:
1. This is a desktop?
2. Your radeon card has HDMI, DVI and VGA?
3. When connecting the HDMI and DVI, is the VGA connection already being used?

---

### Post by eugeds on 2013-07-17
> **jp734 said:**
> okay. few questions:
1. This is a desktop?
2. Your radeon card has HDMI, DVI and VGA?
3. When connecting the HDMI and DVI, is the VGA connection already being used?

thanx for the reply

1: yes is a desktop
2 no, i have HDMI, DVI and DP. The Vga connector is not present
3 No, i not have the VGA connection. normaly i use DVI and work fine. But when connect a HDMi connector all monitors show no signal message, and black screen.. same problem when connect only the HDMI monitor. :confused:

If i use windows 8 all monitors work fine without problems. The graphic  card apparently no have problems. For me is a driver problem, i use the amd/ati catalyst driver. do you have any idea?

thanx

---

### Post by Mark Phelps on 2013-07-17
I have a similar situation -- in that my card has HDMI, DVI, and VGA connectors -- and the documentation clearly states that you can NOT use DVI and HDMI at the same time.  To get two screens (which I have), I had to connect one to the VGA port and use a VGA-to-DVI adapter for the flat panel monitor.  Yours may have the same limitations.

---

### Post by eugeds on 2013-07-17
OK, but if i connect only the hdmi without a another DVI monitor, the HDMI monitor not work. The problem is the HDMI in general, not only when is with a DVI monitor.

---

### Post by jp734 on 2013-07-17
You have a card with displayport so your card is capable of handling 3 screens at the same time. What driver is being used? "lspci -k" will show you if you are using.

---

### Post by eugeds on 2013-07-18
> **jp734 said:**
> You have a card with displayport so your card is capable of handling 3 screens at the same time. What driver is being used? "lspci -k" will show you if you are using.

Yes, in Windows 8 i use 2 monitors in the same computer and that work fine. 

The driver is fglrx_pci


```

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Device 836d
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
    Kernel driver in use: pcieport
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 8445
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
    Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Kernel driver in use: uhci_hcd
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM,P5LD2-VM Mainboard
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
    Kernel driver in use: lpc_ich
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
    Kernel driver in use: ata_piix
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
    Subsystem: ASUSTeK Computer Inc. P5KPL-VM Motherboard
    Kernel driver in use: ata_piix
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Redwood XT [Radeon HD 5670/5690/5730]
    Subsystem: PC Partner Limited / Sapphire Technology Radeon HD 5670
    Kernel driver in use: fglrx_pci
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series]
    Subsystem: PC Partner Limited / Sapphire Technology Device aa60
    Kernel driver in use: snd_hda_intel
02:00.0 Ethernet controller: Qualcomm Atheros AR8131 Gigabit Ethernet (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device 83fe
    Kernel driver in use: atl1c


```

---

### Post by jp734 on 2013-07-18
Hmm, strange ... Your card should have worked just fine. Honestly out of clue. 

Have you used their catalyst? And if you're using open-source driver, I'll give proprietary a shot.

AMDs forum is a good place too.

---

### Post by eugeds on 2013-07-18
Yes i use their catalys.

ok, now write on AMD forum

thanx:)

---

