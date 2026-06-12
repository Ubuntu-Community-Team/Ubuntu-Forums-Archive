---
title: "Lucid - SiS-grrrrrraphics problem!!"
date: 2010-05-01
forum: Hardware
---

### Post by pingu1 on 2010-05-01
Hi!

I just upgraded from 9.10 to lucid, and then lost my 1024x768 resolution.
I now have 800x600... :(

My xorg.conf:
> 
Section "Device"
    Identifier    "Configured Video Device"
        Driver           "sis"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSectionlshw:
> *-pci
          description: Host bridge
          product: 671MX
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:d0000000-d3ffffff
        *-pci:0
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:9000(size=4096) memory:d4000000-d40fffff memory:c0000000-cfffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 771/671 PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                width: 32 bits
                clock: 66MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff(prefetchable) memory:d4000000-d401ffff ioport:9000(size=128)
        *-isa
             description: ISA bridge
             product: SiS968 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list emulated
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) lspci:
> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 04)


---

### Post by pingu1 on 2010-05-01
bump

---

### Post by mhgsys on 2010-05-01
(you need the new driver_)

for sis  771/671 on ubuntu 10.04 have a look here; 
[http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38)

ps; please response in the thread I've linked you to, instead of this one.. to many people are opening new threads, making it difficult to keep track of them and finding solutions. 
The thread I'm linking you to exists since 2008 and is still very active.. it contains lots of contributing users using the sis 771 671 on ubuntu.

---

### Post by mhgsys on 2010-05-03
> **pingu1 said:**
> Hi !
I just wanna say thank you so very much for the brilliant step-by-step guide to fixing my graphics issues. I got some trouble trying to get the new driver, but I figured that somehow the xorg.conf.new was not replacing the xorg.conf file after typing the commands in the guide, so I just copied the file myself - so it replaced the original xorg.conf - and voilà! 

Thans so very much. :) :)

Your welcome, 
Nice to know it's working now.

(The reason I'm posting this here and not in the sis thread is because it's only my response to your thank you note, and it won't have any value for other users to read my response to you)

---

### Post by shadowlin on 2010-05-12
With vesa driver, you can get 1024x768... :)

---

