---
title: "Is it posible to install ubuntu linux in Compaq presario v3425au ?"
date: 2008-03-31
forum: Hardware &amp; Laptops
---

### Post by rimzyak on 2008-03-31
Processor 
AMD Athlon™ 64 X2 Dual-Core Mobile Technology TK-53 (1.7 GHz, 512KB L2 Cache)
Chipset NVIDIA® C51M and MCP51
Graphics NVIDIA GeForce Go 6150

Display 14.1-inch WXGA High-Definition** BrightView Widescreen Display

Standard Memory Two user-accessible SODIMM Slots, up to 4GB DDR2 max system memory (Dual Channel Memory Support***)

Hard Drive With hard drive up to 160GB

Optical Drive 24X DVD/CD-RW Combo Drive, LightScribe SuperMulti 8X DVD±RW with Double Layer Support and  SuperMulti 8X DVD±R/RW with Double Layer Support

Networking/Wireless High speed 56K modem, Integrated 10/100 LAN, broadcom WLAN with Bluetooth option

External Card Expansion ExpressCard slot/54 slot (supports both 34 and 54 form factors)

Media Card Integrated 5-in-1 digital memory reader slot (xD, SD, MMC, Memory Stick and Memory Stick PRO)

Optional Accessory HP xb3000 notebook expansion base, HP Notebook QuickDock, HP 12-cell and 6-cell battery

I/O Ports VGA, USB 2.0 (3), IEEE 1394, Consumer IR, RJ-11, RJ-45, headphone, microphone jack, Omni-directional microphones (2).




the drivers used in vista are:-



 				   				   				   				 
	
Conexant HDAUDIO Soft Data Fax Modem with SmartCP Driver

Conexant High-Definition Audio Driver

NVIDIA nForce Chipset Driver

NVIDIA GeForce Go 6150 Graphics Driver

HP Quick Launch Buttons

Synaptics Touchpad

Software Support for HP Integrated Module with Bluetooth Wireless Technology (Microsoft Windows Vista)

Broadcom Wireless LAN Driver for Microsoft Windows Vista

Support Software for HP Integrated Module with Bluetooth Wireless Technology (Microsoft Windows Vista)

Ricoh 5-in-1 Card Reader Host Controller and Driver

WinFlash for HP Notebook System BIOS (for Notebooks with AMD Processors) - Microsoft Windows/Vista-Based

HP Quick Launch Buttons Critical Security Update



If i am installing ubuntu , will it install suitable drivers for these devices?

Please help me out.

I am planning to try ubuntu linux


rimzy

---

### Post by balaknair on 2008-03-31
You could get the Ubuntu Live CD and try it out without installing. It'll give you a pretty good idea about what works out of the box and what doesn't.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Most of the hardware seems OK and will be supported in Ubuntu, you might want to install nVidia proprietary drivers(by enabling restricted drivers after install). I'm not sure about Dialup 56K modem(software winmodem?) and WiFi(Broadcom seems to have issues with Linux). You might also need to tweak sound a bit in Gutsy with Conexant HD Audio.

Hope this was helpful.

---

