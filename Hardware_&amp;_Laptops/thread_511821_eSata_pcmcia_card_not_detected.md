---
title: "eSata pcmcia card not detected"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by daveappendix on 2007-07-28
Hi.

I've got an Acer Aspire 5672 WLMi laptop, and I'm trying unsuccessfully to get my external SATA drive to work. The first hurdle appears to be that my Silicon Image SiI 3112 SATALink Controller PCMCIA card isn't being detected. The drive enclosure lets me use usb too, and that works ok, but I want the speed of sata.

Please find attached output from lsmod lspci lspcmcia and dmsg. You may notice this in dmesg output:

```
pccard: CardBus card inserted into slot 0
```

This happens when if it's all plugged in on boot. The disk connected to the card powers up when I insert the card, and that will give the same message in dmesg as above.

I can see the cardbus controller ok:

```
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
```

It all works fine in Win XP. Here's all the info I could find about the card there:
SiI 312 Rev2
PCI Bus 11 device 0
IRQ 20
PCI\VEN_1095&DEV_3112&SUBSYS_31121095%REV_02\5&3276D943&0&0048F0

Cheers for any help,
Dave.

p.s. Why is the upload limit for a txt file 19.5K? What's the point? It seems so arbitrary when other types are allowed much larger.

---

### Post by daveappendix on 2007-07-29
Well, it seems to have solved itself. All I did was remove bluez-pcmcia-support (don't need it) and pcmcia-cs (apparently, it's deprecated), then went to try getting things working, one last time. I did lspci again, just for fun, and there it was. The card was detected. I fired up the disk, and hey presto, everything works. Maybe uninstalling those packages cleared up some conflict, but I don't know.

Cheers anyway.

Dave.

---

### Post by daveappendix on 2008-07-02
This problem with my Silicon Image eSata PCMCIA card has resurfaced. I recently installed Hardy Heron, and so when I started up with the card plugged in for the first time (since installing Hardy) tonight, I was happy to see it 'just worked'. I'd had a lot of bother with it with Feisty, and was hoping the upgrade would make my problems melt away.

Well, the honeymoon lasted about an hour. When I restarted the computer after dinner, I noticed that the card was no longer recognised. I didn't change anything, so why would it stop working?

lspcmcia doesn't help:

```
dave@manuel:~$ sudo lspcmcia -v -v
[sudo] password for dave: 
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:0a:09.0)
	Configuration:	state: on	ready: yes
			Voltage: 3.3V Vcc: 3.3V Vpp: 3.3V
			Available IRQs: 3, 4, 5, 6, 7, 10, 11
			Available ioports:	0x00000100 - 0x000003af
						0x000003e0 - 0x000004cf
						0x000004d8 - 0x000004ff
						0x00000820 - 0x000008ff
						0x00000a00 - 0x00000aff
						0x00000c00 - 0x00000cf7
			Available iomem:	0x000c0000 - 0x000fffff
						0x60000000 - 0x60ffffff
						0xa0000000 - 0xa0ffffff
						0xb0400000 - 0xb04fffff
  CardBus card -- see "lspci" for more information

```

lspci doesn't list the card anywhere:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

I would have expected to see something like this in there:

```
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)

```

lsmod shows no sign of sata_sil, and modprobing sata_sil makes no difference.

What should the normal boot sequence be? Yenta sees the card, triggers udev, loads module, etc. I'm not familiar with the pci loading sequence.

Any help greatly appreciated.
Cheers,
Dave.

---

### Post by vahtenberg on 2008-07-23
Has you solved this problem?

---

