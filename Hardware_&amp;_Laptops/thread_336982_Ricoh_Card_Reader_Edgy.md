---
title: "Ricoh Card Reader Edgy"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by mejrum on 2007-01-12
I have a card reader Ricoh R5C822, in a dell e1405/640m laptop. I've tried a sony memorystick  with no success. Running Edgy, kernel 2.6.17-10-generic. 

lspci:
02:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

dmesg output from loading modules sdhci, wbsd, mmx_core: 
[17184953.220000] ACPI: PCI interrupt for device 0000:02:01.1 disabled
[17184965.464000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17184965.464000] sdhci: Copyright(c) Pierre Ossman
[17184965.464000] sdhci: SDHCI controller found at 0000:02:01.1 [1180:0822] (rev 19)
[17184965.464000] ACPI: PCI Interrupt 0000:02:01.1[B] -> GSI 18 (level, low) -> IRQ 66
[17184965.464000] mmc0: SDHCI at 0xdf9fd400 irq 66 DMA
[17187579.512000] wbsd: Winbond W83L51xD SD/MMC card interface driver, 1.5
[17187579.512000] wbsd: Copyright(c) Pierre Ossman

I've searched the forums, with no success. Followed the tips to restart the modules:
$modprobe -r sdhci
$modprobe -r mmc_core
$modprobe mmc_core
$modprobe sdhci

and to enable interrupt:
sudo setpci -s 02:01,1 4c.b=0x02
I don't know if the above line actually works, when I restart the modules after running the command, dmesg still says: 
[17184953.220000] ACPI: PCI interrupt for device 0000:02:01.1 disabled


Nothing in dmesg when I insert the memorystick. 

help me

---

### Post by VuDu on 2007-02-24
Same here...

SD cards work just fine, but MemorySticks are ignored. :(

---

### Post by MonXX on 2007-06-09
Hi, I have a ASUS A6 laptop with an internal card reader and the same problem. lspci gives the following about the Ricoh chip controlling it:

03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)

lspc -vvn:

03:01.0 0607: 1180:0476 (rev b3)
        Subsystem: 1043:1367
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at df800000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
        Memory window 0: 50000000-53fff000 (prefetchable)
        Memory window 1: 54000000-57fff000
        I/O window 0: 0000e000-0000e0ff
        I/O window 1: 0000e400-0000e4ff
        BridgeCtl: Parity+ SERR+ ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

03:01.1 0c00: 1180:0552 (rev 08) (prog-if 10 [OHCI])
        Subsystem: 1043:1367
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min, 1000ns max)
        Interrupt: pin B routed to IRQ 20
        Region 0: Memory at df7ff000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME+

03:01.2 0805: 1180:0822 (rev 17)
        Subsystem: 1043:1367
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin C routed to IRQ 21
        Region 0: Memory at df7ff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-

03:01.3 0880: 1180:0592 (rev 08)
        Subsystem: 1043:1367
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 5
        Region 0: Memory at df7ffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME+

The cardreader is able to read SD cards with the sdhci module. However, Memory Sticks won't work. If I do lshw the Memory Stick sub system has no driver:

*-system:1 UNCLAIMED
             description: System peripheral
             product: R5C592 Memory Stick Bus Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 1.3
             bus info: pci@03:01.3
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: iomemory:df7ffc00-df7ffcff irq:5


I have looked through google and the forums for a while, but I can't find a driver for this. Am I overlooking something, are there any beta drivers out there to test, or should I acknowledge the fact that I can only use SD cards?

I'm running Feisty 7.04 with 2.6.20-16-generic kernel.

---

### Post by TutoWRM on 2007-06-20
same here i have the
Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
and only the sd works, not even the mmc card, that under edgy worked :/
i've tried the sudo setpci -s nn:nn.n 4c.b=0x02 but nothing happens even if a load the modules :/

---

### Post by vbmds on 2007-06-23
Same here, I've got an Asus Z92T (A6T)...

---

### Post by runemaste644 on 2007-09-15
Same... Lenovo 3000 N100... I dont have an MMC card anyway.

---

### Post by bbrg548 on 2007-11-26
Same problem. SD works, MemoryStick doesn't. I don't have any of the other card types to test.

HP Pavilion dv9628nr
Gutsy
Ricoh R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev22)

-Jake

---

### Post by t-dome on 2007-11-29
The same here. I have an Asus F3Tc under Ubuntu Gutsy.

I have a m2 micro card (the memory stick pro duo's successor) with an MMC adapter and it isn't recognized.

My data:

        *-system:0
             description: Generic system peripheral
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 1.1
             bus info: pci@0000:05:01.1
             version: 19
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci latency=64 module=sdhci
        *-system:1 UNCLAIMED
             description: System peripheral
             product: R5C843 MMC Host Controller
             vendor: Ricoh Co Ltd
             physical id: 1.2
             bus info: pci@0000:05:01.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-system:2 UNCLAIMED
             description: System peripheral
             product: R5C592 Memory Stick Bus Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 1.3
             bus info: pci@0000:05:01.3
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0

---

### Post by mezhaka on 2008-01-05
has anyone succeded with starting the MS?

---

### Post by Haluci on 2008-02-20
I have the same thing on a dell e1405, xD cards don't work.

---

### Post by sergiom99 on 2008-03-16
hey guys, same here, only can read SD and no MS or MS-PRO. works great in XP.

> sergio@kubuntu:~$ sudo lspci |grep Ricoh
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)


---

### Post by KillaW0lf04 on 2008-05-09
has anyone found a solution to this? Or is a solution even on the way?

---

### Post by Sam Lars on 2008-06-07
I'm asking the same question... :(

---

### Post by phision on 2008-06-08
:(:(:(:(
same here, vostro 1400

---

