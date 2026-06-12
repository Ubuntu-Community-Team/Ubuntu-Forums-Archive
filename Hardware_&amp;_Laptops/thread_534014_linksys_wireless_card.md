---
title: "linksys wireless card"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by freeztech on 2007-08-24
I have a linksys wireless card wpc54g and it is not working at all with ubuntu 6.10 on a sony viao pcg-f560
I and new to linux
can some one help me

---

### Post by moore.bryan on 2007-08-24
[I]what's the output of ```
lspci
iwconfig
``` in a terminal?
[/I]

---

### Post by freeztech on 2007-08-24
something like
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

with the card in the system

---

### Post by moore.bryan on 2007-08-25
*and of ```
lspci
```?*

---

### Post by freeztech on 2007-08-26
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 FireWire (IEEE 1394): Sony Corporation CXD3222 i.LINK Controller (rev 02)
00:09.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)
00:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem (Mob WorldW SmartDAA) (rev 01)
00:0c.0 CardBus bridge: Ricoh Co Ltd RL5c478 (rev 80)
00:0c.1 CardBus bridge: Ricoh Co Ltd RL5c478 (rev 80)
01:00.0 VGA compatible controller: Neomagic Corporation NM2380 [MagicMedia 256XL+] (rev 10)

---

### Post by moore.bryan on 2007-08-26
[I]that output shows your wireless card isn't loading at startup, so you should use the native windows driver (download it [here]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&packedargs=sku%3DWPC54G&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230042300B01&displaypage=download")) and follow the ndiswrapper tutorial [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

if you run into any issues, just post.
[/I]

---

