---
title: "serial PCCARD adapter"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by ruschi on 2006-06-14
I am trying to get a serial adapter running with my thinkpad t60. 
 I have the pcmcia package installed and setserial as well. Here is a problem description:
 for some odd reasons I have devices /dev/ttyS(0-4) without any serial interface on my thinkpad (T60 comes without only available with docking station) serial interface, IR port and bluetooth are disabled in BIOS anyway. the only thing still active in BIOS is the modem.  I need a serial port to interface a evaluation board.
 I tried both custom and prepackaged kernel
 if I do cat /dev/ttySx I get
```

cat: /dev/ttyS0: Input/output error 

```   
besides how should it behave??
here is what dmesg says when I plug in my serial adapter card in the slot
```

[4296196.995000] pccard: CardBus card inserted into slot 0
[4296196.995000] DEV: registering device: ID = '0000:16:00.0'
[4296196.995000] PM: Adding info for pci:0000:16:00.0
[4296196.995000] bus pci: add device 0000:16:00.0
[4296196.995000] pci: Matched Device 0000:16:00.0 with Driver serial
[4296196.995000] PCI: Enabling device 0000:16:00.0 (0000 -> 0003)
[4296196.995000] ACPI: PCI Interrupt 0000:16:00.0[A] -> GSI 16 (level, low) -> IRQ 201
[4296196.995000] ACPI: PCI interrupt for device 0000:16:00.0 disabled

```
and here is what lspci -vv tells me about my serial adaptercard:
 
```

0000:15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
        Subsystem: Lenovo: Unknown device 2012
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 0x10 (64 bytes)
        Interrupt: pin A routed to IRQ 201
        Region 0: Memory at e4300000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
        Memory window 0: e0000000-e1fff000 (prefetchable)
        Memory window 1: e6000000-e7fff000
        I/O window 0: 00009000-000090ff
        I/O window 1: 00009400-000094ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt- PostWrite+
        16-bit legacy interface ports at 0001

0000:16:00.0 Serial controller: Oxford Semiconductor Ltd OXCB950 Cardbus 16950 UART (prog-if 06 [16950])
        Subsystem: Oxford Semiconductor Ltd: Unknown device 0001
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 201
        Region 0: I/O ports at 9010 [size=8]
        Region 1: Memory at e6000000 (32-bit, non-prefetchable) [size=4K]
        Region 2: I/O ports at 9000 [size=16]
        Region 3: Memory at e6001000 (32-bit, non-prefetchable) [size=4K]
        Region 4: Memory at e6002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 1
                Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0+,D1-,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```

has anyone got a serial pcadapter card running? any help appreciated. 
If not can anyone tell me what usb-serial converter works flawlessly?  

 T.i.a.
 Thomas

---

### Post by ehomo on 2006-09-07
its not working under linux
i still use usb serial adapter

---

