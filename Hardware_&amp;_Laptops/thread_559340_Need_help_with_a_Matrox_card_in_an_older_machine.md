---
title: "Need help with a Matrox card in an older machine"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by maace on 2007-09-20
This is turning into a disease...I'm spending waaay too much time looking for old parts, and I'm obsessed with getting my metaphorical '67 Oldsmobile running again.  But for the moment, I'm just happy to find other addicts out there.

"Hi, my name is 'Maace' "


I put xubuntu 7.04 on this dinosaur... 

Gateway gp6333c
Desktop Intel 333 MHz Celeron MMX Slot 1 Processor SAC
Intel Pentium II Slot 1 LX MicroATX Motherboard
256 MB 100Mhz 64Bit 4-clock CL=2 SDRAM UNBUFFERED DIMM 
30GB + 10GB IDEs


And VIDEO is my current focus.  PC came with:
ATI Rage Pro Turbo Accelerated Graphics Port (AGP) 2X. (on-board graphics)
4 megabytes (MB) of 100 MHz SGRAM on the motherboard

...and now I want to make thegreat leap forward to: (drum roll)
 a Matrox Millennium 4GB PCI card

I have two questions:
1) how does one install (even a generic) Matrox driver in xubuntu?
I couldn't find (in xubuntu) anything like ubuntu's "Hardware Information" 

2) Am I wrong to think that the PCI card will improve performance (possibly only marginally)?
Reasoning:
  a. 4GB of 220MHz on the PCI card should be faster than Mobo's 4GB 100MHz SGRAM
  b. offloading any graphics processing to a PCI card should lower the CPU load (part of me doubts this because despite being on-board, the Mobo graphics are still a dedicated GPU and should already be leaving the CPU alone (until it maxes out, anyway)


I'll upgrade to a better PCI card eventually, - this is just an academic exercise for some noob learning.


Matrox Specs
[http://review.zdnet.com/graphics-cards/matrox-mga-millennium-graphics/4507-8902_16-208795.html?tag=ut](http://review.zdnet.com/graphics-cards/matrox-mga-millennium-graphics/4507-8902_16-208795.html?tag=ut)

Mobo video specs: [http://support.gateway.com/s/MOTHERBD/INTEL/m00335/M0033525.shtml](http://support.gateway.com/s/MOTHERBD/INTEL/m00335/M0033525.shtml)[here]("http://support.gateway.com/s/MOTHERBD/INTEL/m00335/M0033525.shtml")

---

### Post by maace on 2007-09-24
okay... xubuntu is SEEING the Matrox card, but I don't know what is meant by the status 'UNCLAIMED'.  

As per mobo manual instructions, I've changed the BIOS to look for a PCI card in addition to the on board graphics, but device stays 'unclaimed'.  Having a monitor plugged into the VGA output of the matrox card doesn't make a difference, either.

Does anyone have any ideas?
(is this thread still active?)

This is what a 'lshw' shows:


gp6333c-desktop           
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 256MB
     *-cpu
          product: Celeron (Mendocino)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.6.0
          size: 350MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 128KB
     *-pci
          description: Host bridge
          product: 440LX/EX - 82443LX/EX Host bridge
          vendor: Intel Corporation
          physical id: f8000000
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
          resources: iomemory:f8000000-fbffffff
        *-pci
             description: PCI bridge
             product: 440LX/EX - 82443LX/EX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 3D Rage Pro AGP 1X/2X
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 5c
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: latency=66 mingnt=8
                resources: iomemory:f5000000-f5ffffff ioport:9000-90ff iomemory:f4100000-f4100fff irq:9
        *-isa
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE latency=64
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:1000-100f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk:0
                   product: QUANTUM FIREBALL CX10.2A
                   vendor: Quantum
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 9787MB
              *-disk:1
                   product: QUANTUM FIREBALL EX6.4A
                   vendor: Quantum
                   physical id: 1
                   bus info: ide@0.1
                   logical name: /dev/hdb
                   capacity: 6149MB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: PHILIPS CDD3610 CD-R/RW
                   vendor: Philips
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=64
             resources: ioport:1020-103f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0
             resources: irq:9
        *-multimedia
             description: Multimedia audio controller
             product: ES1371 [AudioPCI-97]
             vendor: Ensoniq
             physical id: c
             bus info: pci@00:0c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ENS1371 latency=96 maxlatency=128 mingnt=12
             resources: ioport:1040-107f irq:11
        *-network
             description: Ethernet interface
             product: LNE100TX [Linksys EtherFast 10/100]
             vendor: Lite-On Communications Inc
             physical id: d
             bus info: pci@00:0d.0
             logical name: eth0
             version: 25
             serial: 00:a0:cc:37:01:e7
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=tulip driverversion=1.1.14 ip=192.168.1.104 latency=66 maxlatency=56 mingnt=8 multicast=yes
             resources: ioport:1400-14ff iomemory:f4000000-f40000ff irq:10
        *-display UNCLAIMED
             description: Display controller
             product: MGA 2064W [Millennium]
             vendor: Matrox Graphics, Inc.
             physical id: f
             bus info: pci@00:0f.0
             version: 01
             size: 8MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga_palette
             configuration: latency=0
             resources: iomemory:f4004000-f4007fff iomemory:f6000000-f67fffff irq:11

---

### Post by Kratos on 2007-09-24
Well, if you aren't afraid of the command line, you can collapse to a tty session (Ctrl+Alt+F[1-5]), login and issue the following.

```


sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start


```

That will manuallly reconfigure Xorg and let you choose the card you want and the display driver to use.

---

### Post by maace on 2007-09-25
Ok thanks!  I'll try that after some visitors leave this weekend.

---

### Post by K.Mandla on 2007-09-25
Hi. I split off your question to a different thread in hopes that more people will see it and offer suggestions. 

For my own part, I would suggest editing xorg.conf and changing the "Driver" section to the vesa driver, which should give you enough video output to troubleshoot the system.

I used a Millenium II card in a desktop machine about nine months ago, and there was an issue with the driver then -- the actual driver itself wasn't working. I don't know if it has been ironed out yet or not.

Good luck!

---

