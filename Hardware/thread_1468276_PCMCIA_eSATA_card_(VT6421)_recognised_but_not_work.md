---
title: "PCMCIA eSATA card (VT6421) recognised but not working"
date: 2010-05-01
forum: Hardware
---

### Post by Canuknucklehead on 2010-05-01
G'day,

I've run out of inspiration and was wondering if anyone has any ideas on how to get a PCMCIA eSATA card working in my laptop.

The card in question is a Lindy 51345 eSATA-150 Cardbus Adapter.  The laptop is my old reliable Twinhead Durabook 14K.

I am currently running 9.10 Karmic Koala with the latest updates.

Ubuntu recognises the PCMCIA card when it is plugged in but does not see any drives attached to it.

Some system details:

```
**uname -a**
Linux Twinhead 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 x86_64 GNU/Linux

``````
**lspci**
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
02:00.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)

``````
**lspci -v -v -v**
02:00.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE RAID Controller (rev 50)
    Subsystem: VIA Technologies, Inc. VT6421 IDE RAID Controller
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at 1420 [size=16]
    Region 1: I/O ports at 1430 [size=16]
    Region 2: I/O ports at 1440 [size=16]
    Region 3: I/O ports at 1450 [size=16]
    Region 4: I/O ports at 1400 [size=32]
    Region 5: I/O ports at 1000 [size=256]
    Expansion ROM at 40000000 [disabled] [size=64K]
    Capabilities: [e0] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: sata_via
    Kernel modules: sata_via

``````
**lspcmcia -v -v -v**
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:00:0a.0)
    Configuration:    state: on    ready: yes
            Voltage: 3.3V Vcc: 3.3V Vpp: 3.3V
            Available IRQs: 3, 6, 10
            Available ioports:    0x00000100 - 0x000003af
                        0x000003e0 - 0x000004ff
                        0x00000820 - 0x000008ff
                        0x00000a00 - 0x00000aff
                        0x00000c00 - 0x00000cf7
            Available iomem:    0x000c0000 - 0x000fffff
                        0x60000000 - 0x60ffffff
                        0xa0000000 - 0xa0ffffff

``````
**pccardctl status**
Socket 0:
  3.3V 32-bit PC Card

``````
**pccardctl ident**
Socket 0:
  no product info available

``````
**pccardctl info**
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
```Maybe I've missed something setting up the card...  Would the lack of product information be part of the problem? I could not find any Linux drivers for this device on the VIA or Lindy website.  Can I manually enter the product information?

Note the external drives I'm using for testing are formatted (NTFS and ext3) and work correctly connected via USB.  However they are not visible when connected via eSATA.

Thanks a million in advance for your help - it's appreciated!

---

### Post by pigphish on 2010-06-30
same problem here.

---

### Post by paulwb on 2011-01-22
I have the same problem. Are there any news regarding this, any hints?

---

### Post by pigphish on 2011-01-24
try this command, it works for hotplugged expresscards for me: 

```
sudo modprobe acpiphp
```

---

### Post by paulwb on 2011-01-25
Thanks. This seems to work for ejecting/inserting the card to be recognized again. I can insert this module only if the card is inserted at boot time, otherwise I get "No such device".

But it does not recognize the connected hard disk.

---

