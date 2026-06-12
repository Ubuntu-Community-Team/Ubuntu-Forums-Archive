---
title: "Internal Card Reader Issues"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by haykuro on 2007-05-27
I have an hp zv5000 (a.k.a. the anti-linux laptop). and i've gotten almost everything to function except 1 thing thats been bothering me now.

I have a built in card reader (SD-MS/Pro-MMC-SM).

when i put a card in, under my old non-existent anymore because ubuntu has taken my heart, windows installation a little green light would light up indicating a card has been placed into the slot.

but when i put a card in now, it doesnt do anything..

incase you guys need:
output of "lspci | grep Texas*"
```

02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

```
these are all my reader.


output of lspci:
```

00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

```

EDIT:: yes i read the readme, and understand it may be buggy due to kernel. but i've seen on google some that have gotten it to work, but all described same reasoning for most of the stuff on my laptop, god just was nice.

EDIT2:: i found a website that might help me out via google .. i'll post my results in a bit.
[http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working#Texas_Instruments_5-in-1_Multimedia_Card_Reader_.28SD.2FMMC.2FMS.2FMS_PRO.2FxD.29](http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working#Texas_Instruments_5-in-1_Multimedia_Card_Reader_.28SD.2FMMC.2FMS.2FMS_PRO.2FxD.29)

EDIT3:: didn't seem to do anything.. i added the modules "tifm_sd" and "tifm_7xx1" to /etc/modules and didn't seem to accomplish anything at all.

EDIT4:: im running feisty

---

### Post by treesurf on 2007-05-27
If you're running feisty this howto might help you out:

[http://ubuntuforums.org/showthread.php?t=420721&highlight=card+reader+feisty](http://ubuntuforums.org/showthread.php?t=420721&highlight=card+reader+feisty)

There's also a howto for edgy but I don't have the link for it anymore.  A quick search should turn it up.

---

### Post by haykuro on 2007-05-27
thank you very much, right now i have to run out to olive garden, and when i get back ill try it out and post how it went :)

---

### Post by haykuro on 2007-05-27
ran the installer, no errors, but nothing happened after inserting a card.
i rebooted and still nothing.

---

### Post by haykuro on 2007-05-31
i guess no one can help me with this issue? i really dont want to have to dual boot windows just for my card reader. :(

---

### Post by lstroud on 2007-07-18
did you ever get a resolution to this?

---

### Post by thingswelostinthefire on 2007-10-08
we all have the same problem... i've tried to ask again here: [http://ubuntuforums.org/showthread.php?p=3498015#post3498015](http://ubuntuforums.org/showthread.php?p=3498015#post3498015)

I hope for a response, I don't know what to do!

---

### Post by CWayne on 2007-10-28
Hi,
I have a Toshiba A75 S229, Feisty Fawn.
Same problem you all have, I googled the heck out of this but no joy so far.
I have to dual boot for rosetta stone and Sailing Navigation programs anyway so I'm not too put out at present.
It would be nice if someone finds an answer
Cliff

---

### Post by phenest on 2007-11-04
Same on a Compaq TC1100. Should this chipset be supported, and has anyone reported this to launchpad?

---

