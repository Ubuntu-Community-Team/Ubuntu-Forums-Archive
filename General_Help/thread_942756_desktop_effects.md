---
title: "desktop effects"
date: 2008-10-09
forum: General Help
---

### Post by bradpurvis on 2008-10-09
when i try to enable them it says desktop effects could not be enabled

---

### Post by fooman on 2008-10-09
do you have your video drivers installed?

...what video card or do you have?

---

### Post by roger_1960 on 2008-10-09
Hi

Start here:

[http://www.psychocats.net/ubuntu/desktopeffects](http://www.psychocats.net/ubuntu/desktopeffects)

It is likely that you will need to upgrade your graphics driver file.

---

### Post by bradpurvis on 2008-10-09
i went to restricted drivers and they didn't show up...

---

### Post by imperius69 on 2008-10-09
whats your card? many are blacklisted.

---

### Post by Kevbert on 2008-10-09
If you card is Intel, ATI or Nvidia desktop effects will work in most cases.  Anything else isn't supported. If you enter
```
lspci
```
in terminal its the last item displayed.

---

### Post by bradpurvis on 2008-10-09
aaron@aaron-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controlle

---

### Post by bradpurvis on 2008-10-09
> **Kevbert said:**
> If you card is Intel, ATI or Nvidia desktop effects will work in most cases.  Anything else isn't supported. If you enter
```
lspci
```
in terminal its the last item displayed.

crap sorry i didn't read the end

---

### Post by imperius69 on 2008-10-09
try 

lshw in the terminal

---

### Post by bradpurvis on 2008-10-09
```
aron-desktop:~$ lshw
WARNING: you should run this program as super-user.
aaron-desktop             
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 447MiB
     *-cpu
          product: AMD Sempron(tm)   3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.10.0
          size: 2GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: VT8378 [S3 UniChrome] Integrated Video
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=32 mingnt=2
        *-communication:0 UNCLAIMED
             description: Communication controller
             product: V.92 56K WinModem
             vendor: Agere Systems
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32 maxlatency=14 mingnt=252
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_via latency=32 module=sata_via
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_via latency=32 module=pata_via
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-communication:1 UNCLAIMED
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:11:d8:10:b4:be
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=64.130.166.156 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-scsi
       physical id: 1
       bus info: scsi@5
       logical name: scsi5
       capabilities: scsi-host
       configuration: driver=usb-storage
```


that is what i got

---

### Post by Therion on 2008-10-09
> VT8378 [S3 UniChrome] Integrated Video
vendor: VIA Technologies, Inc.
I'm 99% sure your VIA UniChrome (integrated graphics chipset) will not run Compiz.

---

### Post by bradpurvis on 2008-10-09
> **imperius69 said:**
> try 

lshw in the terminal

hey i replyed 1 hour ago is there anything else you can do to help me?

---

### Post by Yellow Pasque on 2008-10-09
Sorry, but you don't have a video accelerator capable of running Compiz.
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DStatus](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DStatus)

You have a VIA machine and VIA doesn't put any resources into the open-source community (hiring developers, funding open-source projects). VIA is pretty evil; it doesn't cooperate with other companies.

---

### Post by roger_1960 on 2008-10-09
Hi

I have the same chipset and problem.  The nearest I have got to a solution is the driver on [www.viaarena.com](www.viaarena.com) for CLE266 (which suits your chip) but for Gutsy 7.10  It doesnt work with Hardy 8.04.  I am waiting for viaarena to come up with an update ........... unless anyone knows better??

---

### Post by imperius69 on 2008-10-09
> **bradpurvis said:**
> hey i replyed 1 hour ago is there anything else you can do to help me?

dude, be cool, i dont live in front of the computer :cool:

but seems the other users have replied to you.

for that card you will have to wait for the proper driver it seems.

---

### Post by fjgaude on 2008-10-09
Seems that 

```
description: VGA compatible controller
product: VT8378 [S3 UniChrome] Integrated Video
vendor: VIA Technologies, Inc.
```

the **S3 UniChrome** video may not be supported with any advanced drivers that are needed for the desktop effects.

---

### Post by presence1960 on 2008-10-09
I know how you feel. Before I started using Linux, I wanted better AERO effects in Vista. Unfortunately with an integrated video setup there is not much you can do to improve except to buy a video card. You can find some pretty cheap nowadays. I have an Nvidia GeForce 8600GT and it has more than enough to handle desktop effects and Compiz. I bought that from tiger back in May, after my rebate it cost $69. For the price of a video card upgrade you will be really pleased at the results for such a small investment.

---

### Post by cardv on 2008-10-09
thanks for help

---

### Post by presence1960 on 2008-10-09
P.S. just make sure before you buy a video card it will work in ubuntu. I used EnvyNG for my card and it worked great.

---

### Post by Kevbert on 2008-10-10
Unfortunately your card doesn't support 3d acceleration.  There was a Unichrome project in Sourceforge which was working on that goal I believe, but I think the the project may have been suspended.
Your best bet for graphics enhancements/toys are things like screenlets, emerald, etc. Take a look at [http://gnome-look.org/](http://gnome-look.org/)

---

