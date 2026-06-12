---
title: "Micro SD Card Reader"
date: 2015-06-08
forum: Hardware
---

### Post by allenchristophertools on 2015-06-08
So here's my initial blurb about the problem, maybe it gives insight.  this is so funny, I was working on compiling some scripts a few nights ago and then went to sleep, when I woke up my laptop was shut off, so I've been working on other projects since then and now I came back to trying to get back to working on the scripts again and I can't. I had a removable micro SD card that I was creating a usable archive (because of the way that the piece of hardware works the scripts operate the device) so I was creating a directory  listing of each script and to make the device organized and usable while also compiling each of the scripts, but that's beside the point, what I was doing when I went to sleep was that I was logged onto the drive's directory in a shell so my assumption is that the was being written and that the device's file somehow got corrupted... (note to self maybe I should look for the device file somewhere and try to restore it) the card works fine in a usb card reader.. tho there were signs of corruption which I already fixed.       [br] 	 System Information  	[br] Manufacturer: LENOVO 	[br] Product Name: 20327 	[br] Version: Lenovo Miix 2 11 	[br] Serial Number: WB14759635WB0405230N 	 UUID: 36E82115-E326-11E3-800A-0F445BF17DED 	 Wake-up Type: PCI PME# 	 SKU Number: LENOVO_MT_20327 	[br] Family: IDEAPAD  [br]  [http://pastebin.com/tPnDbVUa](http://pastebin.com/tPnDbVUa)   [br]Windows driver information from support.lenovo.com Genesys Card Reader Driver for Windows 8.1 (64-bit) - Lenovo Miix 2 11 Tablet   [br] lsusb and lspci do not show a media reader or a usb device like they usually do when I insert the card dmesg doesn't display anything when I insert the card I tried booting with the card inserted and also removing and reinserting

---

