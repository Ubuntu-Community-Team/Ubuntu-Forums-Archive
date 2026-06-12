---
title: "pcmcia card driver for flash memory card"
date: 2011-02-26
forum: Hardware
---

### Post by n8nt on 2011-02-26
I have an old ATMEL AT5FC008 flash memory card that I'd like to be able to read. I installled Ubuntu on an old HP Pavilion zd2020 laptop (runs nice) and inserted my pcmcia card into the slot.

When I run the pccardctl command  I get this:
bob@bt-linux-lt:/etc$ pccardctl status
Socket 0:
  5.0V 16-bit PC Card
  Subdevice 0 (function 0) [unbound]

I get this when I run lspci:
bob@bt-linux-lt:/etc$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev ff)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV31M [GeForce FX Go5600] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:01.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
02:01.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
bob@bt-linux-lt:/etc$ 

and finally I get this when I insert the card into the slot and then use the dmesg command:
bob@bt-linux-lt:/etc$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev ff)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV31M [GeForce FX Go5600] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:01.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
02:01.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
bob@bt-linux-lt:/etc$ 

I had earlier searched for a windows driver for the card but could not find one. So then I searched for Linux drivers but could not find one.

The card is an 8-megabyte flash memory PCMCIA Card and all I want to do is read the contents and then copy onto another card of the same type. I don't know that much about Linux hardware, but when looking at the pccardctl status above it appears to me that their is no driver. I thought maybe there is some generic driver that might work and if so how would I get it and install it? Thanks for any help.

Bob

---

