---
title: "Unclaimed Hardware, help please?"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by CyberCod on 2007-02-01
I'm setting up Ubuntu for a friend on an older machine.  I accidently had the modem disabled in the bios while installing, and now, after turning it on, lshw shows it to be there, but unclaimed.  

As well as a couple other hardware devices, such as ISA and serial port.

Is there anything that can be done?

below is the output of lshw

```


family
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 126MB
     *-cpu
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.8.3
          size: 700MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse
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
          product: 82810E DC-133 GMCH [Graphics Memory Controller Hub]
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 82810E DC-133 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             size: 64MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: driver=i810_smbus
             resources: iomemory:f8000000-fbffffff iomemory:ffe80000-ffefffff irq:11
        *-pci
             description: PCI bridge
             product: 82801AA PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801AA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801AA IDE
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:ffa0-ffaf
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   product: MDT MD1000JB-00CRA1
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capacity: 93GB
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   product: CR-487ETE
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
        *-usb
             description: USB Controller
             product: 82801AA USB
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:ef80-ef9f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb:0
                   description: Mouse
                   product: Microsoft 3-Button Mouse with IntelliEye(TM)
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@1:1
                   version: 3.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
              *-usb:1
                   description: USB hub
                   product: USB HUB
                   vendor: Winbond Electronics Corp.
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.05
                   capabilities: usb-1.10
                   configuration: driver=hub maxpower=100mA slots=4 speed=12.0MB/s
                 *-usb:0
                      description: USB hub
                      product: TUSB2040/2070 Hub
                      vendor: Texas Instruments, Inc.
                      physical id: 1
                      bus info: usb@1:2.1
                      version: 1.10
                      capabilities: usb-1.10
                      configuration: driver=hub maxpower=100mA slots=4 speed=12.0MB/s
                    *-usb
                         description: Keyboard
                         product: Microsoft Internet Keyboard Pro
                         vendor: Microsoft Corp.
                         physical id: 1
                         bus info: usb@1:2.1.1
                         version: 1.11
                         capabilities: usb-1.10
                         configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
                 *-usb:1
                      description: Generic USB device
                      product: WUSB11 V2.6 802.11b Adapter
                      vendor: Linksys
                      physical id: 2
                      bus info: usb@1:2.2
                      version: 1.00
                      capabilities: usb-1.10
                      configuration: driver=at76c503-rfmd maxpower=500mA speed=12.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: 82801AA SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             resources: ioport:efa0-efaf irq:10
        *-multimedia
             description: Multimedia audio controller
             product: 82801AA AC'97 Audio
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH
             resources: ioport:e400-e4ff ioport:ef00-ef3f irq:10
        *-communication UNCLAIMED
             description: Modem
             product: 82801AA AC'97 Modem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             resources: ioport:e800-e8ff ioport:ec00-ec7f irq:10
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0c:41:0f:6d:fa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=172.16.1.37 wireless=IEEE 802.11-DS



```

Thanx in advance for the help.

---

### Post by CyberCod on 2007-02-01
Can someone at least tell me what it means for hardware to be "UNCLAIMED"?

Does it mean IRQ's not set up properly? or drivers not present? or hardware not supported?

Someone toss me a bone...  give me an idea where to begin looking.

---

### Post by DaveArb on 2007-02-01
[http://ezix.org/project/wiki/HardwareLiSter](http://ezix.org/project/wiki/HardwareLiSter)

*Each node has its individual status: it be CLAIMED (potentially usable) or UNCLAIMED (no driver has been detected for this node), ENABLED (this device is supported and can be used) or DISABLED (this device is supported but has been disabled)*

Looks like "drivers not present".

---

