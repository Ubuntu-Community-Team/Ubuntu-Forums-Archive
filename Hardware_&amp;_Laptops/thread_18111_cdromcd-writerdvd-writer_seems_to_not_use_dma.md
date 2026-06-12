---
title: "cdrom/cd-writer/dvd-writer seems to not use dma"
date: 2005-03-04
forum: Hardware &amp; Laptops
---

### Post by henla464 on 2005-03-04
Hello!

I can't watch dvds, the dvd starts to play but plays very slowly and choppy. After a few seconds the player crashes.

I beliveve this is because DMA is not on:
```

hdparm /dev/hdc

/dev/hdc:
 HDIO_GET_MULTCOUNT failed: Invalid argument
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
```

So naturally I try to enable DMA:
```
 hdparm -d1 /dev/hdc

/dev/hdc:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Operation not permitted
 using_dma    =  0 (off)
```

I run as it as root and still i don't have permission?

The computer I have is a Shuttle 85SN85G4V2 with a AMD64 processor. I run ubuntu for amd64. I have one SATA drive, no ide drives (only the dvd on ide). The ide controller is NForce3 (as indicated below).

```
 lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
0000:00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
0000:00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
0000:00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
0000:00:05.0 Ethernet controller: nVidia Corporation nForce3 Ethernet (rev a5)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
0000:00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
0000:00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:01:07.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technology Inc) Silicon Image Serial ATARaid Controller [ CMD/Sil 3512 ] (rev 01)
0000:02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```


Any suggestions on how I can enable DMA? Could it be lack of support for the ide controller. Do I need a kernel module for it?

Please explain in an easy way, I am new to Linux.

---

### Post by rom on 2005-03-04
Try that:

[PHP]/sbin/hdparm -c 3 -d 1 -X66 /dev/hdc[/PHP] 

You might want to try -c 1 if it gives better results.

Romain

---

### Post by kleeman on 2005-03-04
From a previous post:

I just got this to work by putting

piix
ide-core

ABOVE

ide-cd
ide-disk
ide-generic

in /etc/modules
After rebooting DMA was enabled and dvds now look fantastic

---

### Post by henla464 on 2005-03-04
Thanks for your reply. It didn't help directly but when searching for the previous post you quoted I found the solution. Adding amd74xx to /etc/modules before ide-cd helped!

Summary from posts I read:

VIA Chipset:
Add via82cxxx to your /etc/modules file before ide-cd.
Rboot and set dma with hdparm -d1 /dev/hdx (change x to your drive)

nForce Chipset (and amd):
Add amd74xx to your /etc/modules file before ide-cd.
Rboot and set dma with hdparm -d1 /dev/hdx (change x to your drive)


If you don't have any of the above chipset, do a lsmod to see which modules are loaded. Look at the ide related modules, the module you need to add might be listed there.

---

### Post by kleeman on 2005-03-04
Yeah of course - you are using amd and I am using Intel hence the difference. Enjoy your dvds- they are preety cool on my 21in LCD  :p

---

