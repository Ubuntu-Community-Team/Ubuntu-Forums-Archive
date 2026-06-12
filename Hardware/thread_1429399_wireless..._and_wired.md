---
title: "wireless... and wired?"
date: 2010-03-14
forum: Hardware
---

### Post by FreezWay on 2010-03-14
Ok, so my neighbors windows computer went kaplooie and they lost the system32 folder. I backed everything up to their external hard drive and then tried to reinstall windows... Microsoft deems it must not be because the product ID is not valid. Now I install kubuntu (they wanted KDE.) Anyway, installation was a success, except internet. Not even wired worked at their house. The icon in the corner said it was "authenticating" or something then ceased to acknowledge its existence until I unplugged and replugged it.
Now I come home with the computer and wired works.... wireless still does not. When I type "sudo lshw" the last thing it displays is:
```
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1a:92:bf:26:01
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

This makes sense because the wifi light is not on. However, I lack a way to enable it. There is a little wifi tower symbol on the F2 key in blue (aka press fn.) But pressing Fn+F2 doesn't work. However, Fn+DownArrow does (lowers screen brightness.)

Any Ideas?

---

### Post by Ayuthia on 2010-03-14
Do you know the make and model of the wireless card?  If not, can you post the results of:
```

lspci -nn

```

---

### Post by FreezWay on 2010-03-14
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
03:01.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
03:01.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```

---

### Post by Ayuthia on 2010-03-14
If you are getting a wired connection to work, you can first try going into System->Administration->Hardware Drivers and activate the Broadcom b43 option.  It will need an internet connection so that it can download a firmware file to help make the wireless work.  After you restart, it should work.  If it does not, please try the following (in the Konsole) and post the results:
```

sudo modprobe -r b43 b44 ssb wl
sudo modprobe b44 b43
sudo iwlist scan
dmesg|grep b43

```
The first two commands should not produce anything.  In fact, it should disconnect your wired connection and then bring it back.  Then it will also try to bring up the wireless card.  If it works, it should produce wireless sites with the iwlist command.  If it does not, the last command will hopefully let us know what went wrong.

---

### Post by FreezWay on 2010-03-14
that worked... weird, i went to the drivers thingy earlier and it said there were none...

---

### Post by Ayuthia on 2010-03-14
Well, I am glad it worked.  It seems that Hardware Drivers does that sometimes with the Broadcom cards.

---

### Post by bruno9779 on 2010-03-14
> **FreezWay said:**
> that worked... weird, i went to the drivers thingy earlier and it said there were none...

You need to be connected to the net for HWdrivers to work. Probably you went there when the wired connection did not work

---

