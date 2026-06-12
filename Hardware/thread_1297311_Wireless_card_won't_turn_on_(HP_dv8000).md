---
title: "Wireless card won't turn on (HP dv8000)"
date: 2009-10-21
forum: Hardware
---

### Post by [K!nKy] on 2009-10-21
Hello everyone,

So I just installed Ubuntu on my laptop (hp dv8000) and having one big problem. I can't get the wireless card to turn on...

Any suggestions?

Thanks!

---

### Post by Giblet5 on 2009-10-21
Check the hardware drivers (System menu/Administration/Hardware Drivers).

See if your wireless card is listed there.

Some vendors require that you accept their end user license agreement before you use their half-fast code. Ubuntu calls these drivers "restricted" and they must be explicitly installed.

It's annoying, but that is the way it should be. Make it a little painful to use these retarded vendor's strings-attached software and maybe they'll get a clue...

---

### Post by [K!nKy] on 2009-10-22
> **Giblet5 said:**
> Check the hardware drivers (System menu/Administration/Hardware Drivers).

See if your wireless card is listed there.

Some vendors require that you accept their end user license agreement before you use their half-fast code. Ubuntu calls these drivers "restricted" and they must be explicitly installed.

It's annoying, but that is the way it should be. Make it a little painful to use these retarded vendor's strings-attached software and maybe they'll get a clue...

Installed the software without a problem. Now I just need help getting the card to turn on and look for networks (the connect to network button is grayed out and there are no networks listed. If it helps, the WLAN card light is also off.

---

### Post by [K!nKy] on 2009-10-22
Any ideas?

---

### Post by sakundiak on 2009-10-23
can you give us a lspci readout so we can see what type of broadcom card you have?

---

### Post by [K!nKy] on 2009-10-23
> **sakundiak said:**
> can you give us a lspci readout so we can see what type of broadcom card you have?

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
**06:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] **802.11a/b/g PCI Express Transceiver (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by sakundiak on 2009-10-23
Have you tried following any of this thread at all
[http://ubuntuforums.org/showthread.php?t=1272010&highlight=broadcom+4311](http://ubuntuforums.org/showthread.php?t=1272010&highlight=broadcom+4311)
I see that it shows support for that card out of the box with the restricted driver. So have you went into hardware drivers and enabled the restricted driver? Also have you tired this command "sudo iwlist scan" to see if you can see any access points? Sorry i'm just a newbie at this but it didn't look like anyone else was giving you any help.

---

### Post by Fire_Chief on 2009-10-23
Hopefully this is not the case but most HP laptops I've seen have a physical switch to turn the wireless on and off. Does yours have this and is it on?
Again, not trying to be ridiculous just covering bases. :)

---

### Post by Ayuthia on 2009-10-23
Can you also post the results of:
```
lshw -C network
```
Also, which option did you select from Hardware Drivers (b43 or Broadcom STA)?

---

### Post by [K!nKy] on 2009-10-23
Well turned on my laptop this evening and everything is working fine. Thanks for all the help!

---

### Post by hornet64 on 2011-09-09
> **'[K!nKy] said:**
> Installed the software without a problem. Now I just need help getting the card to turn on and look for networks (the connect to network button is grayed out and there are no networks listed. If it helps, the WLAN card light is also off.
 
 
Try downloading the HP Wireless Assistants. Install the software Driver and run. This will light up the wireless button. WLAN - On and Bluetooth - On.

---

