---
title: "PCMCIA memory card reader w/ 12.04 LTS"
date: 2013-11-09
forum: Hardware
---

### Post by jmdea78 on 2013-11-09
Greetings Ubuntu Forums community,

I have a Toshiba Satellite A100-493 model PSAA9E-0PC047GR.  I would like to read PCMCIA memory cards with its internal PCMCIA slot, but so far, no luck...  I merely wish to copy the data to my local hard drive--maybe I'm just missing the connection on how to mount this type of media. 
 
Would be happy for any kind of assistance or advice anyone might have...  Thanks!

-- Jon

uname -a:
```
Linux judi-Satellite-A100 3.2.0-55-generic-pae #85-Ubuntu SMP Wed Oct 2 14:03:15 UTC 2013 i686 i686 i386 GNU/Linux

```
dmesg output after inserting a SRAM PCMCIA memory card:
 ```
pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
 pcmcia_socket pcmcia_socket0: cs: memory probe 0xde010000-0xde0fffff: excluding 0xde0fe000-0xde10bfff
 pcmcia 0.0: pcmcia: registering new device pcmcia0.0 (IRQ: 3)
 pcmciamtd 0.0: pcmcia: could not parse base and rmask0 of CIS

```
lspcmcia output, card inserted:
```
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:07:06.0)
Socket 0 Device 0:    [-- no driver --]    (bus ID: 0.0)

```
pccardctl status output, card inserted:
```
Socket 0:
  5.0V
 16-bit
 PC Card
  Subdevice 0 (function 0) [unbound]

```
pccardctl ident output, card inserted:
```
Socket 0:
  product info: "PRETEC
", "  2MB SRAM CARD
", "", ""

```
pccardctl info output, card inserted:
```
PRODID_1="PRETEC
"
PRODID_2="  2MB SRAM CARD
"
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
```

lspci output:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

```

---

