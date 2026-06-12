---
title: "[SOLVED] Help me to install restricted drivers"
date: 2008-08-23
forum: General Help
---

### Post by crazyfuturamanoob on 2008-08-23
I want the restricted nvidia drivers. I don't have any drivers installed yet. Nothing. And I got Ubuntu Hardy Heron.

So, could you help me, and give me instructions, how to install the correct restricted driver for my graphics card?
I got Acer Aspire 7520g laptop, and its graphics card is NVIDIA GeForce 8600M GS. Last time I tried to do it without
proper instructions, I almost completely screwed up my ubuntu installation. So could give me as precise instructions as possible?

Edit: I can't see ANYTHING in System->Administration->Hardware Drivers.

Edit2: Output of "lspci":
```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

My respect and huge thanks to the guy who solves this.

Computer is as important as breathing to me.

---

### Post by mb_webguy on 2008-08-23
Go to System->Administration->Hardware Drivers.  Do you see any drivers listed?  If so, check the box next to it to install it.  Once it's installed, restart X with Ctrl-Alt-Backspace.

If nothing's listed there (and something really should if you have an nVidia card), then we'll do it the somewhat less easy way...

---

### Post by crazyfuturamanoob on 2008-08-23
> **mb_webguy said:**
> Go to System->Administration->Hardware Drivers.  Do you see any drivers listed?  If so, check the box next to it to install it.  Once it's installed, restart X with Ctrl-Alt-Backspace.

If nothing's listed there (and something really should if you have an nVidia card), then we'll do it the somewhat less easy way...
There isn't any drivers.

---

### Post by mb_webguy on 2008-08-23
Ok...  Post the output of "lspci".

---

### Post by crazyfuturamanoob on 2008-08-23
> **mb_webguy said:**
> Ok...  Post the output of "lspci".

I edited my first post and added it there.

---

### Post by oldos2er on 2008-08-23
Have a read here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by mb_webguy on 2008-08-23
Yeah... EnvyNG might be the easiest way to go, if not necessarily the best.  (I don't like running foreign scripts on my computer, even ones as well-known as trusted as Envy.)

The driver package you need is nvidia-glx-new.  You could install the package and then reconfigure xorg.conf, but EnvyNG would do everything for you.

---

### Post by Tony_photoplus on 2008-08-23
I have had some experience now and I have just loaded GEforce2 MX/MX 400 Nvidia card.  
I used this link
[http://https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("http://https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

This is handy as well

[http://ubuntuguide.org/wiki/Ubuntu:Hardy]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")

I have one problem though and thats is there is no min/max or x on my screen now.

Tony

---

### Post by nbayiha on 2008-08-23
Give a try to this thread.

[http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787)

---

### Post by crazyfuturamanoob on 2008-08-24
[size="7"]wohoooooooo i works!!!!!!!! Thankyou i love youuu[/size]

edit: sorry, i really had to.. but the new desktop effects with compiz ROCK!! awesome I will never use windows again

---

