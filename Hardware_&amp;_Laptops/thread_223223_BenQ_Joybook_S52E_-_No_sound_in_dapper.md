---
title: "BenQ Joybook S52E - No sound in dapper"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by NeoRc on 2006-07-26
The sound-card work good in Windows. But It cannot work correctly in dapper. 
```
# lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:01.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:06:01.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:06:03.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
0000:06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

The brand of the sound card is "CONEXANT AMR AC-Link 2 Channel". There's a text file in the driver, and make a description of the device:
```
SmartMC?& AC-Link Modems

Conexant Offers a Family of AC-Link Modem and Audio/Modems to Support Mobile and Desktop Applications

Conexant¡¯s SmartMCTM and SmartAMCTM system solutions provide the lowest system costs, improved time to market and enhanced features and performance. The product family includes all the necessary hardware and software (algorithms and drivers) required to support modem-only or audio/modem solutions. The Conexant AC-Link system solutions support a wide range of architectures including PCI card or Mini PCI designs, digital controllers or core logic solutions incorporating digital audio and modem support.



Motherboard designs include desktop solutions using the advanced communications riser (ACR), audio modem riser (AMR) or communications network riser (CNR) connectors, and notebook designs using the mobile daughter card (MDC) or Mini PCI connector, or custom form factors. Conexant played an important role in the definition of the AMR and MDC specifications and has helped define the majority of core logic solutions introduced on the market.



Motherboard configurations using the ACR, AMR, CNR, MDC or mini PCI architectures simplify the modem homologation process by allowing the card to be certified independent of the actual system motherboard design. These architectures also support the ability to remove all analogue circuitry from the motherboard, leading to higher-quality audio and reduced motherboard complexity.



The SmartMC and SmartAMC system solutions meet the PC 99 System Design Guide specifications, offering significant benefits such as better overall system performance and standards based power-management support.

These solutions provide all the features of Conexant¡¯s industry-leading SoftK56TM software modem. The communications control code for the SmartMC and SmartAMC are also equivalent to other Conexant modem products. This common control code allows OEMs that have already tested the HSF modem with their standard applications to move quickly into production with the Smart MC and SmartAMC. In addition to standard modem features, both chipsets offer Caller ID, enabling users to identify the source of incoming calls. The chipsets also feature Wake-On-Ring functionality, allowing PCs in a low-power, suspended state to automatically turn back on after receiving a phone call. This unique feature enables PCs to receive incoming messages that they would otherwise miss. Conexant¡¯s modem codec fully supports Intel¡¯s AC 97 version 2.1 specification, designed to help PC manufacturers adopt new modem technologies more quickly and cost-effectively. Conexant collaborated with Intel to develop this specification, and contributed key modem technology.



Because the modems are software based, they can be upgraded for value-added features such as standards, simply by downloading the appropriate drivers.



SmartMC

SmartMC is Conexant¡¯s first product to incorporate our patented SmartDAATM technology, which enables modems and other communications devices to be programmed for use on any public phone network worldwide. The SmartMC modem codec device set supports analogue data communications at up to 56 kbps, analogue fax at 14.4 kbps, and voice/remote telephone answering machine (TAM). SmartMC also supports AC-Link (AV 97) operation for ACR, AMR and CNR interface and MDC and Mini PCI applications. Enhanced features such as monitoring of local extension status without going off-hook are also supported. The device set consists of a host side device (HSD) in a 48-pin TQFP, and a line side device (LSD) in a 32-pin TQFP.



Features

Advanced Power Management

Fax Modem

   - V.17, V.29, V.27ter, and V.21 ch 2

   - EIA/TIA 578 Class 1 and T.31 Class 1.2 commands

Voice, telephony (TAM and SP models)

   - TIA-695 command set

   - 8-bit m-Law/A-law/linear coding

   - 8000 Hz sample rate

   - TAM support with concurrent DTMF detect, ring detect and Caller ID

V.80 synchronous access mode supports host-controlled communication protocols

   - H.324 interface support

V.8/V.8bis and AT commands

(V25ter with Annex A)

Full-duplex speakerphone (FDSP) mode

   - Loop gain control, transmit and receive path AGC

Data/Fax/Voice call discrimination

Multi-county support

   - Call progress, blacklisting

Caller ID single profile stored in host

System compatibilities

   - Windows 95, Windows 95 OSR2, Windows 98, Windows NT 4.0, Millennium, WindowsWin2k operating systems

   - Microsoft¡¯s PPC 98 Design Initiative-compliant

   - Unimodem/V compliant

AC-Link

   - AC97 2.1

   - ACR 1.0

   - AMR1.01

   - CNR 1.0

   - MDC 1.0

   - Mini PCI 1.0

Supports PCI bus power management

   - ACPI power management registers

   - PME APM support

+3.3V operation with +5v tolerant digital inputs

+5V or +3.3V analogue operation

SmartMC

Device packages:

   - SmartMC: 48-pin TQFP

   - LC in 32-pin TQFP

SmartAMC

Combined Audio/Modem codec (AMC)

   - AC 97 codec V2.1 compliant (AMC 97)

Audio

   - Stereo full-duplex codec with 18-bit resolution

   - Three audio analogue input channels

   - Two audio analogue output channels

   - One S/P DIF output channel

   - Delta-Sigma Converter for enhanced performance

   - Soft SRC

   - Soft Digital Mixing

   - Soft HRTF-3D (A3D)

   - Soft EAX 1.0/2.0

   - Conexant¡¯s EndlessWave Technology

Full-duplex speakerphone (FDSP) mode (SP models)

   - Switching to/from data, fax and DSVD

   - Soft microphone gain and muting

   - Soft speaker volume control and muting

   - Soft adaptive acoustic, line and handset echo cancellation

   - Soft acoustic echo cancellation concurrent with DSVD

Device packages

   - SmartAMC: 48-pin TQFP



Available Parts

SmartMC II 	 

SmartMC II/S 	Speakerphone

SmartMC II/P 	Conexant Player

SmartMC II/EHRTF 	HRTF + EAX

SmartMC II/MAX 	SP + Conexant Player + HRTF + EAX

SmartMC II/W 	 

SmartMC II/WS 	Speakerphone

SmartMC II/WP 	Conexant Player

SmartMC II/WHRTF 	HRTF + EAX

SmartMC II/WMAX 	SP + Conexant Player + HRTF + EAX
```

---

