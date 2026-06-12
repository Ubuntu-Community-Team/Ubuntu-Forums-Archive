---
title: "SD/MMC/MS/MS PRO Card Reader not working for an ASUS Z71V"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by tschak909 on 2006-06-22
I have an ASUS Z71V Sonoma laptop, with a built in 4-in-1 card reader that can read the following card types:

* SD
* MMC
* MS
* MS Pro

when I insert the card, nothing appears to happen from the desktop perspective, but I get the following from my dmesg:

Jun 22 20:56:11 localhost kernel: [17263519.756000] pccard: PCMCIA card inserted into slot 0
Jun 22 20:56:11 localhost kernel: [17263519.756000] pcmcia: registering new device pcmcia0.0

lspci gives me the following data:

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6600] (rev a2)
0000:03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
0000:03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:03:01.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:03:01.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
0000:03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG MiniPCI Adapter (rev 05)


-------

the PCMCIA cardbus bridge is a Yenta, and it is mapping into the following areas:

[17179597.812000] pcmcia: parent PCI bridge Memory window: 0xfea00000 - 0xfeafffff
[17179597.812000] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8cffffff

so there are definitely two pcmcia slots, and the memory card reader is mapping onto one of them...

Loading the sdhci module directly doesn't seem to make a difference, although it does load into memory....

Has anyone had luck with this particular configuraiton?

-Thom

---

### Post by StevenYap on 2006-06-25
Your Asus laptop uses the Ricoh chipset which does not support the SDHCI protocol. Ricoh also doesn't give out specifications on how to use their controller. So, no card reader support on laptops with the Ricoh chipset. 

I'm in the same boat as you are as my Asus S5N also uses a Ricoh chipset. Sorry.

---

### Post by balak on 2006-06-26
[QUOTE=StevenYap]Your Asus laptop uses the Ricoh chipset which does not support the SDHCI protocol. Ricoh also doesn't give out specifications on how to use their controller. So, no card reader support on laptops with the Ricoh chipset. 

I'm in the same boat as you are as my Asus S5N also uses a Ricoh chipset. Sorry.[/QUOTE]

Is that really true :(

My Dell X300 also has the Ricoh chipset and I was hoping to be able to read my mmc card through it.

The funny thing is, I was forced to boot back to windoze after more than 8 months for this part and XP didn't have a driver for this sd card reader :)

---

### Post by danzvash on 2006-06-26
Not all Ricoh chipsets are created equal.

If you don't see a "0805" in your lspci output you are not supported by SDHCI.

See:
[http://list.drzeus.cx/pipermail/sdhci-devel/2006-June/001021.html](http://list.drzeus.cx/pipermail/sdhci-devel/2006-June/001021.html)

Otherwise, if you have this ... :
```
0000:01:03.2 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
0000:01:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
0000:01:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 03)
```

... you should be able to get the sdhci module running.
The new "audit" patch referred to on the sdhci mailing list (linked above) should apply cleanly to 2.6.17 kernel trees.

---

### Post by loko on 2006-07-08
i can agree that some card-readers with rico-chipset work.

i have: ```
0000:06:03.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:06:03.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:06:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:06:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

And SD-Cards work for me, BUT MCC-Cards DONT work.

---

### Post by sirtrent on 2006-07-11
I have an Asus M5N which also uses the Ricoh SD card slot and have been trying to get it too work, when I put a car in my dmesg reacts and gives

[17187627.788000] pccard: PCMCIA card inserted into slot 0
[17187627.788000] cs: memory probe 0xfe700000-0xfe8fffff: excluding 0xfe700000-0xfe71ffff 0xfe8e0000-0xfe8fffff
[17187627.792000] pcmcia: registering new device pcmcia0.0

I don't know if the sdhci dirver will work with my reader ([http://mmc.drzeus.cx/wiki/Linux/Drivers/sdhci](http://mmc.drzeus.cx/wiki/Linux/Drivers/sdhci)) but the problem is that I don't really want to have to compile my own vanilla 2.6.17 kernel.  So basically my question is whether or not there is some other way to use the driver in Breezy (Since the Ubuntu people seem quite satisfied with 2.6.15xxx kernels) with a 2.6.15, perhaps as a module, I can't seem to find one since the sdhci project was included in the kernel project.

lspci give me

0000:01:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:01:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)

---

### Post by AverageFury on 2006-07-21
I've got the same problem with my Samsung Q25.

SD/MemoryStick Card reader is a Ricoh R5c591 or R5c593.
It doesn't work ](*,)

[http://mmc.drzeus.cx/wiki/Controllers/Ricoh/Frontreport](http://mmc.drzeus.cx/wiki/Controllers/Ricoh/Frontreport)

---

### Post by Flying caveman on 2006-11-29
> **balak said:**
> Is that really true :(
....

The funny thing is, I was forced to boot back to windoze after more than 8 months for this part and XP didn't have a driver for this sd card reader :)

That doesn't suprise me.  I have the Asus Z71z  and I laoded windows on it(just to see how it played some games) It took me a few tries because the installer kept hanging-up. when it finally did install all I had was a desktop no sound no ethernet no wireless.  What the hell was taking it so long to do nothing? I got so frustrated with it, I just started from scatch ubuntu only. everything worked with nothing to do on my part except the card readers which I just discovered a while ago.  Oh well, I'll just use the mini usb to download my pictures.  :) 

I love the resolution 1680x1050 resolution on this thing, I'm using mostly salvaged parts out of my toshiba m35x; which finally died after taking it apart and re-soldering the power jack 100 times, hard drive CPU and wireless card are the only things I could move over. but I upgraded my Celeron M 340 to a Pentium M 730 but i'm thinking of putting a 400fsb pentium or Celeron cpu in to see if i can overclock it :mrgreen:

---

