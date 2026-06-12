---
title: "fujitsu lifebook c-5230 display issue"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by DasLemm on 2007-06-09
I was able to install ubuntu 7.04 on an old fujitsu life book i had lying aroud. the only problem it has (other than moving at a snail's pace.) is that the largest screen resolution i can get is 800x600. I previously had XP installed and it ran at a 1024x768 resolution, so i know the display is capable of it.
I've tried messing around with the dpkg-reconfigure a bit, but to no avail.  I have also learned that i dont have the right chipset for the 915resolution package.

```
$ lshw
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 576MB
     *-cpu
          product: AMD-K6(tm) 3D processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 2
          bus info: cpu@0
          version: 5.8.12
          size: 450MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 pge mmx syscall 3dnow k6_mtrr up
        *-cache
             description: L1 cache
             physical id: 0
             size: 64KB
     *-pci
          description: Host bridge
          product: M1541
          vendor: ALi Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: latency=64
        *-pci
             description: PCI bridge
             product: M1541 PCI to AGP Controller
             vendor: ALi Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
        *-usb
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 maxlatency=80
             resources: iomemory:fe000000-fe000fff irq:9
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-multimedia
             description: Multimedia audio controller
             product: M5451 PCI AC-Link Controller Audio Device
             vendor: ALi Corporation
             physical id: 4
             bus info: pci@00:04.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ALI 5451 latency=64 maxlatency=24 mingnt=2
             resources: ioport:1000-10ff iomemory:fe001000-fe001fff irq:9
        *-bridge
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=ali1535_smbus latency=0
        *-isa
             description: ISA bridge
             product: M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: c
             bus info: pci@00:0c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: iomemory:40010000-40010fff irq:9
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1420
             vendor: Texas Instruments
             physical id: c.1
             bus info: pci@00:0c.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5
             resources: iomemory:40011000-40011fff irq:9
        *-display
             description: VGA compatible controller
             product: Cyber 9525
             vendor: Trident Microsystems
             physical id: e
             bus info: pci@00:0e.0
             version: 49
             size: 4MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: latency=64
             resources: iomemory:fe800000-febfffff iomemory:fe020000-fe03ffff iomemory:fe400000-fe7fffff
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: f
             bus info: pci@00:0f.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ALI15x3_IDE latency=0 maxlatency=4 mingnt=2
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:1400-140f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: FUJITSU MHH2064AT
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 5729MB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: MATSHITADVD-ROM SR-8174
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capacity: 282MB
                   capabilities: packet
        *-communication UNCLAIMED
             description: Communication controller
             product: F-1156IV WinModem (V90, 56KFlex)
             vendor: Agere Systems
             physical id: 12
             bus info: pci@00:12.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0 maxlatency=14 mingnt=252
             resources: iomemory:fe002000-fe0020ff irq:9
     *-network
          description: Wireless interface
          product: AR5005G 802.11abg NIC
          vendor: Atheros Communications, Inc.
          physical id: 0
          bus info: pci@06:00.0
          logical name: wifi0
          version: 01
          serial: 00:11:50:d9:71:e5
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list logical ethernet physical wireless
          configuration: broadcast=yes driver=ath_pci ip=198.145.72.14 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
          resources: iomemory:3c000000-3c00ffff irq:9

```
Any help counts. thanks in advance.

---

### Post by jjordan on 2007-06-10
Wow, I could not find anything about this model, the closest I could find was a C-5235.  That has an ATI-rage mobility video "card".  Since the internet does not think your laptop exists then your card probably was not autodetected properly and the generic video driver was installed.  Use Synaptic or Adept or Apt-Get to install the ATI driver.  

-j

---

### Post by DanUSA on 2007-06-10
I have a Fujitsu N-6420 laptop that I just purchased and I am having the same problem. I can't install because the windows are to large. Did you find an answer to the problem? Thanks.

---

### Post by DasLemm on 2007-06-10
JJordan - I got as far as 'sudo apt-get install ati' and then realized that i didn't know which driver i was aiming for...

---

### Post by jjordan on 2007-06-10
I believe the driver you need is the xserver-xorg-video-ati.

sudo apt-get install xserver-xorg-video-ati

Easiest thing to do is reboot (not really needed but easiest for me to dsecribe)  If your card is not detected then you may need to edit your xorg.conf.  There are several threads on that.  What desktop are you using Gnome, KDE or Xfce?  There mey be a graphical tool for you to select the card and set resolution.

- j

---

### Post by jjordan on 2007-06-10
Actually it looks like that driver is installed in a default Ubuntu installation. Post back if apt-get tells you that.

-j

---

### Post by DasLemm on 2007-06-10
yeah, it says that i already have the latest version.

I'm also running gnome.

---

### Post by DasLemm on 2007-06-10
so I tried using the ati selection in '-dpkg-reconfigure -phigh xserver-xorg' and my x server crashed on boot. so i dont know how well ati supports my display...

---

### Post by jjordan on 2007-06-10
Well, I know you are already using the command line because you used apt-get.  Try this gedit /etc/X11/xorg.conf this will open your xorg.conf file in gedit (but will not allow you to save any changes).  What we are looking for is about one-third of the way down and look something like this:

Section "Device"
	Identifier	"DeviceDualLFP"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		0
	Option		"MonitorLayout" "CRT,LFP"
EndSection

The important line is the "Driver"  mine is using the i810 driver (my laptop has an Intel 915).  Send me back what it says on that line.  There may be several blocks like the one above.

-j

---

### Post by jjordan on 2007-06-10
Guess I should have bolded that or something:

Type at the command line:

**gedit /etc/X11/xorg.conf**

-j

---

### Post by DasLemm on 2007-06-10
Ok, so:

Section "Device"
             Identifier          "Generic Video Card"
             Driver                "trident"
             BusID                 "PCI:0:14:0"
EndSection

I've done some more reading on editing the xorg.conf file, and my file has  1280x1024, 1024x768 under all of the modes. So i dont know why it's not detecting the resolutions...

---

### Post by jjordan on 2007-06-10
The reason it is not selecting 1024 X 768 is because it is using a fall back mode of the ATI card that tells the generic drive that it cannot handle it.

First we need to backup your xorg.conf:

**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.cong.generic**

Now we are going to edit your xorg.conf

**sudo gedit /etc/X11/xorg.conf**

replace "Generic Video Card" with "ati"

save the xorg.conf file.

restart xwindows 

**CTRL+ALT+Backspace**

If it does not work it will dump you to a command prompt.  If that happens loggin and than copy the backedup xorg.conf over the edited xorg.conf:

**sudo cp /etc/X11/xorg.conf.generic /etc/X11/xorg.conf**

There are some pretty good howtos out there for the ati cards.  There is also an automated configuration utilities. 

-j

---

### Post by jjordan on 2007-06-10
Wow, sorry for the typo,

Backup:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.generic

---

