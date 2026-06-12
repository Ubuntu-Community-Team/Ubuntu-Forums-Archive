---
title: "Question to Acer owners. Card reader"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by zba78 on 2006-06-20
Has anyone who has a built-in card reader got their's to work? My Aspire comes with a 4-in-1 card reader but I've never really tried to figure ou how to get it to work.

Thanks

---

### Post by tsb on 2006-06-20
Mine works OOTB on my Ferrari 3200.

---

### Post by zba78 on 2006-06-20
So when you stick a memory card in something shows up in your storage devices/desktop?

---

### Post by Lunar_Lamp on 2006-06-20
TSB - could you let me know the output of lspci for your card reader?  I haven't even tried setting mine up as I was told it wouldn't work (acer aspire 5024) - but if I find you have the same/similar hardware I might investigate.

---

### Post by nolongerlivecd on 2006-06-20
Aspire 5504. Doesn't work

User@Ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
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
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
0000:06:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:06:01.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
0000:06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
0000:06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
0000:06:04.2 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
0000:06:04.3 FLASH memory: ENE Technology Inc: Unknown device 0520 (rev 01)
0000:06:04.4 FLASH memory: ENE Technology Inc: Unknown device 0551 (rev 01)

---

### Post by Lunar_Lamp on 2006-06-20
That's the same controller from the one in the aspire 5020 series I think:

```
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
0000:00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38
0000:00:07.0 PCI bridge: ATI Technologies Inc: Unknown device 5a39
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
0000:06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0000:06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:06:06.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
0000:06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

```

For clarity:

```

~$ lspci | grep Texas
0000:06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
**0000:06:06.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller**

```

---

### Post by PvSinNL on 2006-06-20
The built-in card reader on my Aspire 2012WLMi worked out of the box, both in Breezy and now in Dapper.

I've looked at the output of [FONT="Courier New"]**lspci**[/FONT], but don't seem to be able to spot anything related to a card reader, to be honest.
[FONT="Courier New"]**lsusb**[/FONT] gives me this, though:
> Bus 001 Device 004: ID 0d7d:0240 Phison Electronics Corp. I/O-Magic/Transcend 6-in-1 Card Reader

---

### Post by Lunar_Lamp on 2006-06-21
Ah right, it's being recognised as a USB reader, which it appears the kernel has support for.

---

### Post by zba78 on 2006-06-22
Had a look at lspci, seems that the cardreader is recognised as a Texas Instument interrated PCI one. Doesn't work at all.

---

### Post by Neg127 on 2006-06-22
```
mike@smeegil:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
0000:06:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
[B]0000:06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
0000:06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
0000:06:04.2 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)[/B]
0000:06:04.3 FLASH memory: ENE Technology Inc: Unknown device 0520 (rev 01)
0000:06:04.4 FLASH memory: ENE Technology Inc: Unknown device 0551 (rev 01)

```

Acer Aspire 9502WSMI

Card reader is functioning 100%.

---

### Post by nolongerlivecd on 2006-06-22
Mine is the CB-712/4 as well, why doesn't it work?

---

### Post by zba78 on 2006-06-23
Back at a linux box. Here is the output of lspci. Card reader still not working

```
lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
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
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
0000:06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:06:01.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
**0000:06:01.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller**
0000:06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03
```

---

### Post by LostSouLz on 2006-07-14
Im using TM 3280. didnt work too...

```
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
0000:02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)
0000:03:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)0000:0a:06.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:0a:06.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:0a:06.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:0a:06.3 0805: Texas Instruments: Unknown device 803c

```

---

### Post by LostSouLz on 2006-07-15
NE1 found a solution to this??

---

### Post by tiger015 on 2006-07-16
I have Acer Travelmate 4502. My card reader does not work either. Just nothing is detected. Same story was with breezy.

I appreciate any possible solutions.

---

### Post by Rexbron! on 2006-07-16
Adding myself to the list.

My situation is alittle bit different, I have a PCMCIA sandisk compact flash reader. It mounts under media, but refuses to let me access it (complains about it not being in fstab or mtab even after I manually entered it). Possible support here?

---

### Post by LostSouLz on 2006-08-04
Bump!!!](*,)

---

### Post by stevieb on 2006-08-04
i have the same cardreader, a CB-712/4 in a Lenovo 3000 C100 laptop.  Doesn't work.

-steve

---

### Post by evil_elman on 2006-08-05
I've never used the card reader (neither in Windows or Ubuntu). I'll pop down to Jessops later today and by a cheap and small memory card to try it...

```

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
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
0000:01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
**0000:06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller**
0000:06:01.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
**0000:06:01.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller**
0000:06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)

```

**[SIZE="4"]LostZouLz, zba78, nolongerlivecd, Neg127:[/SIZE]**
Since you've got similar chipsets in your laptops could I ask if you guys get the following in your kernel logs during boot?
```

[17179572.348000] PCI: Using ACPI for IRQ routing
[17179572.348000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.348000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179572.348000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179572.348000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179572.348000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179572.348000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179572.348000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179572.348000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179572.348000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179572.348000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
```

**[EDIT]** Came back from Jessops with a cheap 128MB SD card. It works in Windows but not in Ubuntu. Absolutely nothing happens when it's inserted... What could be the logical step as to troubleshooting from here?

---

### Post by Lunar_Lamp on 2006-09-14
For those with the Texas Instruments PCIxx21/x515 Cardbus Controller I think support for it may be now in the 2.6.17 kernel, and backported to 2.6.16:

[http://www.webcon.ca/~imorgan/tifm21/](http://www.webcon.ca/~imorgan/tifm21/)

I'm not sure though, as despite many similarities, my lspci is not identical, and I haven't had chance to upgrade my kernel and check.

---

### Post by tombott on 2006-10-18
Aspire 9500 not working either:
```

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express P rocessor to DRAM Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express R oot Port (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High De finition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 2 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge  (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family ) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X70 0 (PCIE)
0000:06:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 C ontroller (PHY/Link)
0000:06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigab it Ethernet (rev 10)
0000:06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
0000:06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev  10)
0000:06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader C ontroller (rev 01)
0000:06:04.2 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Control ler (rev 01)
0000:06:04.3 FLASH memory: ENE Technology Inc: Unknown device 0520 (rev 01)
0000:06:04.4 FLASH memory: ENE Technology Inc: Unknown device 0551 (rev 01)
```

---

### Post by Lunar_Lamp on 2006-11-01
I THINK I MAY HAVE A SOLUTION!

I cannot test it however as I don't have an SD card to hand.  I take no credit for this whatsoever, but those of you with a "PCIxx21" cardbus may be able to use the solution I found here:

[http://www.linuxquestions.org/questions/showthread.php?t=497403](http://www.linuxquestions.org/questions/showthread.php?t=497403)

I believe you just need to add the command to /etc/rc.local if it works.  That is "sudo nano /etc/rc.local" [substitute "nano" for "gedit" if you prefer a graphical editor] and add in the line it suggests in the forum post on linuxquestions.

I hope this helps people and please report back if it works!  I don't have any way of testing it unfortunately...

---

### Post by quail-linux on 2006-11-03
I have a Acer Aspire 5601AWLMi laptop running Edgy with a 5 in card reader in it and it does show up anything when i put a 16MB SD card into it

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[b]0a:09.0 CardBus bridge: Texas Instruments Unknown device 8039
0a:09.2 Mass storage controller: Texas Instruments Unknown device 803b
0a:09.3 Class 0805: Texas Instruments Unknown device 803c[/b]

```

I have submitted a bug about the problem
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63386](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63386)

---

### Post by Rothguard on 2006-11-04
i have a 5672WLMi running Edgy  no card reader sucess as yet most likely because im NEWB    ill try some things and report back :P

simon@simon-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7145
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)
0a:09.0 CardBus bridge: Texas Instruments Unknown device 8039
0a:09.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
0a:09.2 Mass storage controller: Texas Instruments Unknown device 803b

i dont know what all that means but hopefully someone does :P

---

### Post by Lunar_Lamp on 2006-11-06
Rothguard, you appear to have a similar laptop to quail-linux.  My fix will not work for you as your card-reader is a different model (and doesn't appear to be detected at all).

---

### Post by quail-linux on 2006-11-06
> **Rothguard said:**
> i have a 5672WLMi running Edgy  no card reader sucess as yet most likely because im NEWB    ill try some things and report back :P

simon@simon-laptop:~$ lspci
....
[b]0a:09.0 CardBus bridge: Texas Instruments Unknown device 8039
0a:09.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
0a:09.2 Mass storage controller: Texas Instruments Unknown device 803b[/b]

i dont know what all that means but hopefully someone does :P

Hi,

I not sure if you took notice of my post, but by the looks of it i have the same 5 in 1 cardreader as you.

I have reported a bug about the card reader and it's confirmed as a bug and you will just have to be patient till the developers can get it fully working.

here is part of the bug quoted
> 
inserts and removals to the multi-media-card reader are detected and reported in the Edgy Beta kernel, but not picked up by Ubuntu at higher levels than that, so no mounting. Nor does the device show up in /dev.

lspci output
0a:09.0 CardBus bridge: Texas Instruments Unknown device 8039
0a:09.2 Mass storage controller: Texas Instruments Unknown device 803b
0a:09.3 Class 0805: Texas Instruments Unknown device 803c

dmesg output
[17179586.384000] Yenta: CardBus bridge found at 0000:0a:09.0 [1025:0102]
[17179586.384000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179586.384000] Yenta: Routing CardBus interrupts to PCI
[17179586.384000] Yenta TI: socket 0000:0a:09.0, mfunc 0x01321b22, devctl 0x66
[17179586.432000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17179586.432000] sdhci: Copyright(c) Pierre Ossman


to read more about it refer to this [link]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63386")

**Major Update**

<Edit Tuesday, November 07 2006 at 16:23:27(+1030)>
I found out after compiling the driver from my howto before that the drivers are already part of the kernel and you only have to do what is below.
</Edit Tuesday, November 07 2006 at 16:23:27(+1030)>

**Below has been tested under Edgy 6.10**

**Use at your own risk**

Load the drivers
from terminal type
> sudo modprobe tifm_7xx1
> sudo modprobe tifm_core
> sudo modprobe tifm_sd

Now to insert a SD media card and it should auto mount.

If all went well you can now edit the the /etc/modules file so you can load the drivers for the card reader on boot up

From terminal type
> sudo gedit /etc/modules

Add the drivers to the modules file
> 
tifm_7xx1
tifm_core
tifm_sd

save the file

HTH
Dale

---

### Post by quail-linux on 2006-11-07
> **Rothguard said:**
> i have a 5672WLMi running Edgy  no card reader sucess as yet most likely because im NEWB    ill try some things and report back :P

simon@simon-laptop:~$ lspci
.....
0a:09.0 CardBus bridge: Texas Instruments Unknown device 8039
0a:09.1 FireWire (IEEE 1394): Texas Instruments Unknown device 803a
0a:09.2 Mass storage controller: Texas Instruments Unknown device 803b

i dont know what all that means but hopefully someone does :P

you might want to run this command as well and update your pci.ids file
> sudo update-pciids
and then run lspci again

my unknown devices are now known, heres example
> 
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:09.3 Class 0805: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


HTH
Dale

---

### Post by Rothguard on 2006-11-08
TRULY AWSOME  i shall go forth and spread the word to my fellow newbs

---

### Post by fettmedbobafett on 2006-11-08
Thanks to quail linux for posting the solution! worked like a charm for me under 6.10 with an acer aspirer 5672WLMI \\:D/

---

### Post by mrojas73 on 2006-11-08
Quial thank you so much...this issue has been buging me for a long time and I had almost given up on it.

Thank you again!

---

### Post by quail-linux on 2006-11-08
> **Rothguard said:**
> TRULY AWSOME  i shall go forth and spread the word to my fellow newbs

> **fettmedbobafett said:**
> Thanks to quail linux for posting the solution! worked like a charm for me under 6.10 with an acer aspirer 5672WLMI \\:D/

> **mrojas73 said:**
> Quial thank you so much...this issue has been buging me for a long time and I had almost given up on it.

Thank you again!

It great to hear that this is work around is working for people till the developers fix the problem so the work a round is not need.

I have also written a [Howto wiki page]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5601AWLMi/HowTo") for my laptop that might help out people with other models of Acer laptops

Regards
Dale

---

### Post by quail-linux on 2006-11-09
> **quail-linux said:**
> It great to hear that this is work around is working for people till the developers fix the problem so the work a round is not need.

I have also written a [Howto wiki page]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5601AWLMi/HowTo") for my laptop that might help out people with other models of Acer laptops

Regards
Dale

Hi i forgot to add if you need to reply to things about my Howto/s that is out side of the card reader problem please post your problems to this thread
[http://ubuntuforums.org/showthread.php?t=287928](http://ubuntuforums.org/showthread.php?t=287928)

And i will try to help you the best that i can

Thanks
Dale

---

### Post by Timokl on 2006-11-13
Hey quaillinux, thanx for your fix. Suddenly, my card reader starts to work.

I have an Acer Aspire 5021NWlcI

---

### Post by finite9 on 2006-11-14
I have an Acer Aspire 5021WLMi and I Ubuntu 6.06 amd64.  I have not installed any fixes for my card reader, it just works out of the box:

CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

If I insert an SD card, it pops up automatically on the desktop as "mmcdisk".

---

### Post by cruiseraddict on 2006-11-25
Has anyone with the ENE Tech card reader had any success in getting it working? 
Here is my lspci for the reader
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

---

### Post by darkshadow on 2006-11-27
I just got my card reader in a Acer Travelmate 4404 working using tifm_sd but the trick was according to the tifm modules homepage anyhting over 512mb requires using kernel 2.6.18 which is newer then the one in edgy.

After compiling the new kernel and the source for the tifm modules (they did not come with 2.6.18 from kernel.org) I successfully used my 2GB SD card in the reader.

According to tifm site the problem of no sd cards greater then 512mb was for every card reader not just tifm_sd

Plus a unrelated bonus of no longer requiring special boot parameters to get my wireless working.

---

### Post by WirelessMike on 2006-12-05
Will this work for after-market usb card readers installed in desktops, too?  I have one that has been working with (k)ubuntu since Warty, but sometime during a kernel upgrade in Dapper, it stopped working and hasn't worked since.  Nothing I've tried will make the reader appear at all anymore, neither lspci nor lsusb find anything resembling a card reader, yet up until kernel 2.6.15-23, it worked.

Is this an unrelated bug?  It still just works when I boot into Windows, but Edgy refuses to acknowledge it...

---

### Post by caesar753 on 2006-12-17
> **quail-linux said:**
> Hi,



**Below has been tested under Edgy 6.10**

**Use at your own risk**

Load the drivers
from terminal type


Quote:
sudo modprobe tifm_7xx1
Quote:
sudo modprobe tifm_core
Quote:
sudo modprobe tifm_sd



Now to insert a SD media card and it should auto mount.

If all went well you can now edit the the /etc/modules file so you can load the drivers for the card reader on boot up

From terminal type


Add the drivers to the modules file

save the file

HTH
Dale

Hi all,
i followed the indications above, sent by quail-linux, but it doesn't work out on my Acer Aspire 1637WLMi.
I don't have a sd card but a xd card (i think it's quite different) and my card controller is not Texas Instruments, but ENE technology. I have tried to stick the card in the hole after loading tifm*, but it doesn't work out. I need to activate my card reader because I don't use Windows (but i know that on Windows the card reader works out) and linux (ubuntu edgy 6.10 distro) is my only operating system.

This is my lspci:


00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 1a)
00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:02.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
02:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller
02:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc:

Please help me, i don't know what to do...

Thank you

---

### Post by atasaRossios on 2006-12-19
Also had no luck,
I have Aspire 5680
I notice somenthing strange this is the only device [disabled]?

Here is the lspci:

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 0090
        Flags: bus master, medium devsel, latency 168, IRQ 169
        Memory at d2200000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 88000000-89fff000 (prefetchable)
        Memory window 1: 8a000000-8bfff000
        I/O window 0: 00003400-000034ff
        I/O window 1: 00003800-000038ff
        16-bit legacy interface ports at 0001

06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 0090
        Flags: medium devsel, IRQ 11
        Memory at d2201800 (32-bit, non-prefetchable) [disabled] [size=128]
        Capabilities: [80] Power Management version 2

06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 0090
        Flags: bus master, medium devsel, latency 64, IRQ 177
        Memory at d2201c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 0090
        Flags: medium devsel, IRQ 11
        Memory at d2202000 (32-bit, non-prefetchable) [disabled] [size=128]
        Capabilities: [80] Power Management version 2

06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 0090
        Flags: medium devsel, IRQ 255
        Memory at d2201900 (32-bit, non-prefetchable) [disabled] [size=256]
        Capabilities: [80] Power Management version 2

---

### Post by zba78 on 2007-02-20
I had piratically forgotten about this thread and only stumbled across it by accident. In all reality I had given up on the card reader working in Linux in the near future.

**quail-linux** I thank you for your input as loading the 3 modules you described worked perfectly. Now my memory cards automount each time I put one in.

In all honesty the card reader working or not was never that important (I have a USB card reader anyway) but it's just nice to know/show that Linux compatibility with hardware is improving all the time.

Thanks again for all your input

---

### Post by rpasell on 2007-03-14
I too am having a problem with ENE reader

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)

Has anyone with ENE reader gotten it to work?

Aspire 5102

---

### Post by dptxp on 2007-03-17
I have problem with Acer 5101 , ENE card reader.

---

### Post by UeB on 2007-04-16
I have an acer Aspire 3020

integrated card reader did not work with breezy.
It did work with dapper and
And now with edgy it does not work anymore / again !!!

Or at least automount does not work.

lspci says:

06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

---

### Post by zba78 on 2007-05-09
Just checked yesterday for the first time since upgrading to Feisty and it seems the card reader is no longer working.

I upgraded using the recommended method (i.e. through the update manager) and everything else works perfectly.

Has anyone else who had theirs working before noticed any problems since upgrading to Feisty?

---

### Post by bonzodog on 2007-10-28
i have an Acer travelmate 4200 WLMi, with the 4 in 1 card reader, and it comes up with the ENE flash controller as well.

Has anyone got any ideas about how to make this work?

It does not work with feisty or Gutsy.

---

### Post by atasaRossios on 2007-10-28
I have upgraded to Gutsy and everything works fine for me

---

### Post by jointstereotype on 2007-11-07
I too am having [a problem]("http://ubuntuforums.org/showthread.php?t=589398") with my Acer's built-in ENE card reader. It seems to work just fine with the 256mb SD cards I have, but I get I/O errors whenever I try to use my 2gb SD card (the card is good, only several months old, and gives me no trouble whatsoever under Windows Vista).

If anyone has a trick to make the ENE reader work with 2gb SD cards, it would be much appreciated. ;)

---

### Post by tombott on 2007-11-08
Just to confirm this now works on my Acer Aspire 9500 running Gutsy.

Very happy!

Just to add just tried a 2gb card and this works fine for me.

---

### Post by jointstereotype on 2007-11-08
**UPDATE:** After 2 weeks of null results, I've given up on the ENE card reader for now. LOL I went out and bought a Sandisk USB reader, and though it doesn't always show up when plugged in (lordie, another problem to have to figure out...*sigh*), it mounts / unmounts / writes / reads all my SD cards just fine, and works faster than the ENE did.

--

Hmm...is there any reason an SD card formatted under Windows might need to be reformatted under Linux in order to work properly - and if so, how would I go about doing that? (I'm wondering if the ENE reader doesn't just prefer Linux-formatted cards...?)

---

### Post by ugm6hr on 2007-12-08
My Acer 5051 AWXMi SD card reader almost works in Gutsy....  It wil read files just fine, but won't let me write to them :(

[http://ubuntuforums.org/showthread.php?p=3915373#post3915373](http://ubuntuforums.org/showthread.php?p=3915373#post3915373)

---

### Post by sheleztt on 2008-01-07
Hey :) 
I've started googling about "Damn Card Reader Problem", but
then i plugged it in...
tail -f /var/log/messages
...
Jan  7 10:02:18 sheleztt-laptop kernel: [35614.400000] mmcblk0: mmc1:b368 SDC   1999360KiB
Jan  7 10:02:18 sheleztt-laptop kernel: [35614.400000]  mmcblk0: p1

 AND IT WORKS! JUST OUT OF BOX :) *happy* 
Things are simpler than i thought.
Requisites: up2date Kubuntu 7.10 (damniloveit)
Acer Aspire 5310.
lspci | grep -i ene
06:00.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
06:00.1 Generic system peripheral [0805]: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
06:00.2 FLASH memory: ENE Technology Inc Unknown device 0720
06:00.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller

Good Luck Folks.

---

### Post by linuxadore on 2008-03-19
ENE card reader works out-of-the-box on Acer Aspire 5310

---

### Post by JaredsaNOOB on 2008-03-19
I have a aspire 5570z with a 5-in-1 reader, and mine worked out of the box. when I did the plugin thing it called a texas instruments something orother. I forgot the command to show that list.

---

### Post by AJB2K3 on 2008-03-20
The ene on my 3690 wont read any cards.
Now fully recognised in lspci however what modules are needed at startup because 
etc/modules has nothing for the ene reader.

---

### Post by AJB2K3 on 2008-03-21
Hmn I think I may have found a clue to getting the ene card reader working.
LSPCI =
```
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

```
I hit on the issue being with
```
[CODE]06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
```

After a bit of google, this is the card chipset I have in mine.
So using a command posted on an earler page
```
modprobe CB-712/4

```
I get
```
FATAL: Module CB_712/4 not found.
```
Have I found the issue or am I missing some thing?

---

### Post by tuskenraider on 2008-03-21
i have a 9410z mine works like a charm...  plug a card in...and poof it pops up.. gotta love ubuntu!

tusken

---

### Post by AJB2K3 on 2008-03-21
In that case can I get someones ene module then

---

### Post by dh_an on 2008-04-20
[I]
0a:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0a:02.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
0a:02.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
0a:02.2 FLASH memory: ENE Technology Inc Unknown device 0720
0a:02.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
[/I]

It's the Acer Travelmate 6292.

Works fine for my SD-cards but can't seem to recognize Memory Stick Duo.
Apparently something wrong with the MS Pro Duo part of the driver, the one I have the most use for ](*,)

---

