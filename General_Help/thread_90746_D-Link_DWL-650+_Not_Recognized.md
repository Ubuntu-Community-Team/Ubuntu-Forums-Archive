---
title: "D-Link DWL-650+ Not Recognized"
date: 2005-11-15
forum: General Help
---

### Post by br00tal on 2005-11-15
I've read that this card is supported out of the box under Breezy, but I can't even get it to show up when I do "lspci".  Here's the output:
```
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0000:00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX/741/M741/760/M760 PCI/AGP

```
***NOTE*** That Broadcom Card is integrated and does not function, which is why I bought this D-Link card.  I have tried removing it and it still does not recognize my D-Link card.  This D-Link card is a cardbus card.

So, where do I begin to get Breezy to recognize this card?  I've tried hotplug at boot as well as running it separately.  It just pretends that it isn't there.

Oh, and I have a dual boot, and the D-Link works under Windows just fine, so the card and the cardbus slot work properly.

Thanks,
Jesse

---

### Post by kruz on 2005-11-15
i ahve that same chipset and card
mine works fine went to system>admin tasks> networking

then make SURE you disable your onboard LAN adapter
and enable and config ur ath0(what mine was named)
dlink card

tell me if that works
if not i might be able to get you some wireless scripts

i think i might have modprobe'd something but i dont think i did have to

---

### Post by br00tal on 2005-11-16
The problem is that Linux doesn't even recognize the card's existence.  If I could get the card to show up as being plugged in, then I could probably get it to work.  Anyone else have this issue?

---

### Post by dbott67 on 2005-11-16
I have a D-Link DWL-650+ that uses the acx_pci module.

Here's the output from lspci:
```
dbott@breezy:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
0000:00:04.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 12)
0000:00:05.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:05.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:05.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:05.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:09.0 Communication controller: Toshiba America Info Systems FIR Port (rev 23)
0000:00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 (rev 07)
0000:00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 (rev 07)
0000:00:0d.0 Multimedia controller: C-Cube Microsystems Cinemaster C 3.0 DVD Decoder (rev 02)
0000:01:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
dbott@breezy:~$
```
And from lsmod:
```
dbott@breezy:~$ lsmod | grep acx
acx_pci               122752  0
firmware_class          9472  1 acx_pci
dbott@breezy:~$
```
The driver is located here:
```
dbott@breezy:~$ locate acx_pci
/lib/modules/2.6.12-8-386/kernel/drivers/net/wireless/acx/acx_pci.ko
/lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/acx/acx_pci.ko
dbott@breezy:~$
```
In Warty, I had troubles with the card and used the following commands to get it up & running:
```
sudo modprobe acx_pci
/etc/init.d/networking restart
```

Hope this helps get you going.
-Dave

---

### Post by br00tal on 2005-11-16
Alright, I did all this stuff, and I still got nothing.  For some reason I can't get it to see my card.  The module loaded fine, but still no card displayed in lspci.  Hmm..

---

### Post by br00tal on 2005-11-21
Anyone know what's up with this?  It's as though Breezy just is not reading my cardbus controller properly.

---

