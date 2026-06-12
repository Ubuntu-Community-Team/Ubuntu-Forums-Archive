---
title: "Graphical glitches with Intel 915GM"
date: 2009-01-09
forum: Hardware
---

### Post by melado on 2009-01-09
I have just installed Ubuntu 8.10 and I am getting some weird graphical glitches when pressing any hotkey which makes something appear in the screen.

For example, I press the hotkey to lower the brightess of the screen, it works. In Windows (and before that, in the BIOS for example) an icon appears in the top left corner. In Ubuntu a white square with garbage appears, and some weird glitch runs over the screen.

I know it's difficult to understand, so I made a video. You can see it here: [http://vimeo.com/2776629](http://vimeo.com/2776629)

I remember having this same exact problem in the past with Windows XP, but updating the drivers solved the problem. I don't know if it's there a newer version of the needed drivers for Ubuntu...

The laptop is a Samsung R50, I'll be posting lspci details in a minute.

Edit: here they are
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:07.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
06:09.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
06:09.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
06:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
06:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 03)
```

Edit 2: I uploaded the /var/log/Xorg.0.log because it is quite long to paste it here. Here it is: [http://pastebin.com/f21b97087](http://pastebin.com/f21b97087)

Any ideas? Thanks in advance.

---

