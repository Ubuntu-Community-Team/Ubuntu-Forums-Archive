---
title: "Internal SD card reader doesn't work with gutsy...sort of."
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by bharris25 on 2007-11-07
I have a Toshiba Satellite A105-s4104 laptop with Gutsy and Mint 3.0 dual booted.  My internal 5 in 1 sd card reader won't really work with Gutsy,  works fine with Mint and worked fine with Feisty after the update but with Gutsy if I put an sd card in it recognizes it and it pops up on the desktop and asks if you want to import photos.  I click ignore and when I click on the card it opens the window and sometimes it will will disconnect right there and say unsafe device removal and other times it will stay open until I try to move something from the card and then disconnect, it will usually remount right away.  I have a usb card reader so this is more annoying than anything just don't see why it won't work.

---

### Post by road2elysium on 2007-11-29
> **bharris25 said:**
> I have a Toshiba Satellite A105-s4104 laptop with Gutsy and Mint 3.0 dual booted.  My internal 5 in 1 sd card reader won't really work with Gutsy,  works fine with Mint and worked fine with Feisty after the update but with Gutsy if I put an sd card in it recognizes it and it pops up on the desktop and asks if you want to import photos.  I click ignore and when I click on the card it opens the window and sometimes it will will disconnect right there and say unsafe device removal and other times it will stay open until I try to move something from the card and then disconnect, it will usually remount right away.  I have a usb card reader so this is more annoying than anything just don't see why it won't work.

My internal SD card reader on a Dell Inspiron 700m does pretty much the same thing.  It automounts until I try to grab the data either through Gnome/terminal and then does the unsafe device removal thing.

```
road2elysium@i700m:~$ lspci | grep Texas
02:04.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
02:04.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
02:04.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
02:04.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller

```

---

### Post by holyowned on 2007-12-02
I have a Toshiba M65 laptop with an ENE internal reader.  When I plug an SD card in, the light flashes 5 times, but it doesn't show up in My Computer, or anywhere I have found.
Coding lspci |grep ENE gives:

lspci |grep ENE
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

---

