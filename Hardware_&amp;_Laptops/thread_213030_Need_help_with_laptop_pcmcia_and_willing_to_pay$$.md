---
title: "Need help with laptop pcmcia and willing to pay$$"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by funky_munky on 2006-07-10
Hello I have a Sony PCG-FX150K laptop.  The PCMCIA slots do not seem to work with Kubuntu 6.06 (or Ubuntu for that matter).  I have never been able to get it to work with any linux distro I have tried but I am not the best informed linux user.  I was hoping that someone could help me get it to work.  I am willing to pay $50 US (paypal)to the first person to help me get it to work with my wireless WG511T which I hear works quite well with linux.  The problem is the PCMCIA slots as far as I can tell. 

I have bumped into things that say that for the Sony Vaio PCG-FX150K that ACPI or APIC have to be working first but I am not positive on that.  In order to boot I have to add noapic to my boot options.
  
dmesg |grep pcmcia says:
[   44.897953] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   44.898549] pcmcia: parent PCI bridge Memory window: 0xf4100000 - 0xf41fffff
[   44.898558] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   45.087783] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   45.088379] pcmcia: parent PCI bridge Memory window: 0xf4100000 - 0xf41fffff
[   45.088387] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff


dmesg|grep pci spits out these problems that also might be related:

PCI: No IRQ known for interrupt pin A of device 0000:01:02.0. Please try using pci=biosirq.
[   15.864831] PCI: No IRQ known for interrupt pin B of device 0000:01:02.1. Please try using pci=biosirq.
[   22.228526] PCI: No IRQ known for interrupt pin A of device 0000:01:00.0. Please try using pci=biosirq.
[   43.310183] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.738690] PCI: No IRQ known for interrupt pin A of device 0000:01:02.0. Please try using pci=biosirq.
[   44.898819] PCI: No IRQ known for interrupt pin B of device 0000:01:02.1. Please try using pci=biosirq

Kinfocenter says no pcmcia controller detected.

modprobe pcmcia gives no errors but dmesg at the bottom says:

[ 1911.661978] cs: pcmcia_socket0: cardbus cards are not supported.

anyway let me know what else I need to try and I will honestly pay $50 US to the FIRST person that gets me connected wirelessly through my WG511T in Kubuntu on my Sony PCG-FX150K.  


***It works fine in windows (blah)***

---

### Post by Eversmann on 2006-07-10
please post the result of sudo lshw command with the card to get hardware informatión.

Also, did you try to boot with "irqpoll" added to the kernel line? we could see if it's an irq problem.

EDITED:

Btw, reading what says on dmesg, boot first with pci=biosirq. If no luck, then irqpoll. If still no luck, let's see the lshw for which chipset the pcmcia has.

---

### Post by funky_munky on 2006-07-10
Ok thanks for the quick response.

pci=biosirq seems to have gotten rid of the:

[ 7054.640586] PCI: No IRQ known for interrupt pin A of device 0000:01:02.0. Please try using pci=biosirq.
[ 7054.640657] PCI: No IRQ known for interrupt pin B of device 0000:01:02.1. Please try using pci=biosirq.
[ 7061.079787] PCI: No IRQ known for interrupt pin A of device 0000:01:00.0. Please try using pci=biosirq.
[ 7082.988686] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 7086.114418] PCI: No IRQ known for interrupt pin A of device 0000:01:02.0. Please try using pci=biosirq.
[ 7086.237157] PCI: No IRQ known for interrupt pin B of device 0000:01:02.1. Please try using pci=biosirq.

and replaced it with:

[ 6555.694528] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

But that still does nothing for my PCMCIA setup.

I also tried irqpoll and that seems to have the same end result as what I previously posted except now i see:

[ 9345.223600] hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)

hehe so anyway I think pci=biosirq seems to have fixed something that I didnot know whether or not was a problem :)

Ok so I did lshw and got this:

```

laptop-laptop
    description: Computer
    product: PCG-FX150K(UC)
    vendor: Sony Corporation
    version: N/A
    serial: 28318830-3701332
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=enabled boot=oem-specific frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled
  *-core
       description: Motherboard
       product: PCG-FX150K(UC)
       vendor: Sony Corporation
       physical id: 0
       serial: 28318830-3701332
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: R0205U0 (01/05/01  )
          size: 105KB
          capacity: 192KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.6
          slot: U1
          size: 600MHz
          capacity: 600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 256KB
             capacity: 512KB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 14
          slot: System board or motherboard
          size: 512MB
          capacity: 512MB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 256MB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 256MB
             width: 32 bits
     *-pci
          description: Host bridge
          product: 82815 815 Chipset Host Bridge and Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 82815 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 11
             size: 64MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: driver=i810_smbus
             resources: iomemory:f8000000-fbffffff iomemory:f4000000-f407ffff irq:10
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-firewire UNCLAIMED
                description: FireWire (IEEE 1394)
                product: TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated)
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@01:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                resources: iomemory:f4104000-f41047ff iomemory:f4100000-f4103fff
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 2
                bus info: pci@01:02.0
                version: 80
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:f4106000-f4106fff iomemory:b00502010-b0050200f
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 2.1
                bus info: pci@01:02.1
                version: 80
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus
                resources: iomemory:f4107000-f4107fff iomemory:b00906010-b0090600f
           *-network
                description: Ethernet interface
                product: 82801BA/BAM/CA/CAM Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@01:08.0
                logical name: eth0
                version: 03
                serial: 08:00:46:14:5c:ff
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.14-k4-NAPI duplex=half firmware=N/A ip=64.134.221.195 link=yes multicast=yes port=MII speed=10MB/s
                resources: iomemory:f4105000-f4105fff ioport:3000-303f irq:9
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801BAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
        *-ide
             description: IDE interface
             product: 82801BAM IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1800-180f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: FUJITSU MHM2200AT
                   vendor: Fujitsu
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 5823
                   serial: 01066576
                   size: 18GB
                   capacity: 18GB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma4 smart=on
                 *-volume:0
                      description: W95 FAT32 (LBA) partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 11GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Linux filesystem partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 6675MB
                      capabilities: primary
                 *-volume:2
                      description: Linux swap / Solaris partition
                      physical id: 3
                      bus info: ide@0.0,3
                      logical name: /dev/hda3
                      capacity: 972MB
                      capabilities: primary nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: UJDA710
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.04
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:9
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-23-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             resources: ioport:1810-181f irq:5
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@00:1f.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:2400-241f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-23-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-multimedia
             description: Multimedia audio controller
             product: 82801BA/BAM AC'97 Audio
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH
             resources: ioport:1c00-1cff ioport:1840-187f irq:5
        *-communication UNCLAIMED
             description: Modem
             product: 82801BA/BAM AC'97 Modem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             resources: ioport:2000-20ff ioport:1880-18ff irq:5

```

---

### Post by funky_munky on 2006-07-11
Ok dude you are getting me pretty close.  I did some experimenting last night and the problem does in fact seem to be linked to ACPI.  

I changed the kernel line to say pci=biosirq and removed acpi=off.  When I did that with the netgear card in the lights lit up on the network card.  So that is something I have never done in linux before.

The problem is now that acpi won't let me boot and pci=biosirq don't activate my pcmcia without it.

I am super excited.  It now is looking possible where as before I was disheartened.

So this is what happens.  My computer says uncrompressing kernel or whatever and it starts booting like mad off the harddrive.  About 15 seconds later or so Lights on the Netgear card light up.  The drive continues to boot for a while (no text on screen besides the kernel part) and then the screen goes black, still lit but black.  The harddrive then stops spinning and it just sits there. 

So is there anyway to configure ACPI so that it does some stuff and not other stuff?  Or is there anyway to see boot messages from a failed boot?  Or where do I go now?  The $50 bux is still there for the taking.  Even if I figure it out for myself I will give the money to whoever gave me the clue to lead me to the conclusion.

---

### Post by funky_munky on 2006-07-11
man I thought $50 would finally get someone to help me get this running.  how about begging?  Pleaassseee Heeeelllllpppp  mmmeee!!!!

---

### Post by Ramses on 2006-07-12
You could check if there is bios update for your laptop. Read bios-portion [here]("http://winterwolf.co.uk/vaiopm").

---

### Post by Eversmann on 2006-07-12
Sorry pal i've been out ;-)

Your laptop uses a Ricoh chip that could be problematic. Do these test to get some clues before continue:

- Run cardctl ident to see if the card is recognized by ubuntu. Maybe it's a problem with a power activation by the kernel. If it appears, the card is recognized but there's another problem.

- Download Kanopix live cd and boot with it. If the card works with kanopix we'll know that there's a problem wtih a kernel module, a driver, the current kernel or that of stuff you know.

EDITED:

and boot always with pci=biosirq ;-)

After reading again your first post, the pcmcia slot is actually using the yenta driver. Run the first step i posted to see if ubuntu recognizes the card. This will give a good clue ;-)

---

### Post by Eversmann on 2006-07-12
Please, post your dmesg result too after pluggin in the card. the whole dmesg, thanks.

---

### Post by funky_munky on 2006-07-12
There is no change in dmesg when I plug in the netgear card because the pcmcia controller seems to be dead without acpi.  But if I enable acpi then i can't see because I get a blank screen while booting.

Cardctl don't see anything either and I think its because of the acpi junk.

cardctl ident
Socket 0:
  no product info available
Socket 1:
  no product info available

I really think that if there were some way to configure acpi to change what it does and what it does not that will help.

If there were a way to see any error messages from my failed boots with acpi on then that could help also.

Can acpi be loaded as a kernel module instead of loading at boot?

I will have to give Kanopix a try but I have tried many different livecd's and all of them need acpi=off for me to boot.  I will have to try it later today.

Here is DMESG anyway:
```

[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e5800 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001fe70000 (usable)
[4294667.296000]  BIOS-e820: 000000001fe70000 - 000000001fe7f800 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001fe7f800 - 000000001fe80000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000001fe80000 - 0000000020000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 510MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 130672
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 126576 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI present.
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda2 ro quiet splash pci=biosirq acpi=off
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (013ff000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[    0.000000] Detected 745.495 MHz processor.
[   18.498229] Using tsc for high-res timesource
[   18.499999] Console: colour VGA+ 80x25
[   18.501161] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.502497] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.560546] Memory: 507700k/522688k available (1976k kernel code, 14400k reserved, 606k data, 288k init, 0k highmem)
[   18.560557] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.620071] Calibrating delay using timer specific routine.. 1491.94 BogoMIPS (lpj=745973)
[   18.620147] Security Framework v1.0.0 initialized
[   18.620166] SELinux:  Disabled at boot.
[   18.620199] Mount-cache hash table entries: 512
[   18.620413] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   18.620432] CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   18.620453] CPU: L1 I cache: 16K, L1 D cache: 16K
[   18.620461] CPU: L2 cache: 256K
[   18.620467] CPU serial number disabled.
[   18.620473] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   18.620510] mtrr: v2.0 (20020519)
[   18.620521] CPU: Intel Pentium III (Coppermine) stepping 06
[   18.620531] Enabling fast FPU save and restore... done.
[   18.620538] Enabling unmasked SIMD FPU exception support... done.
[   18.620547] Checking 'hlt' instruction... OK.
[   18.624571] checking if image is initramfs... it is
[   20.681167] Freeing initrd memory: 6606k freed
[   20.718109] NET: Registered protocol family 16
[   20.718230] EISA bus registered
[   20.722190] PCI: PCI BIOS revision 2.10 entry at 0xfd9b0, last bus=1
[   20.722212] PCI: Using configuration type 1
[   20.723361] ACPI: Subsystem revision 20051216
[   20.723369] ACPI: Interpreter disabled.
[   20.723381] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.723400] pnp: PnP ACPI: disabled
[   20.723413] PnPBIOS: Scanning system for PnP BIOS support...
[   20.723486] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7470
[   20.723496] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xa88d, dseg 0x400
[   20.727873] PnPBIOS: 20 nodes reported by PnP BIOS; 20 recorded by driver
[   20.727920] PCI: Probing PCI hardware
[   20.727932] PCI: Probing PCI hardware (bus 00)
[   20.728189] Boot video device is 0000:00:02.0
[   20.728342] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   20.728351] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[   20.729070] PCI: Transparent bridge - 0000:00:1e.0
[   20.730443] PCI: Using IRQ router PIIX/ICH [8086/244c] at 0000:00:1f.0
[   20.734590] pnp: 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   20.734599] pnp: 00:0a: ioport range 0x1000-0x105f has been reserved
[   20.734608] pnp: 00:0a: ioport range 0x1100-0x110f has been reserved
[   20.734616] pnp: 00:0a: ioport range 0x1060-0x107f has been reserved
[   20.734624] pnp: 00:0a: ioport range 0x1180-0x11bf has been reserved
[   20.735067] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   20.735107] PCI: Bus 2, cardbus bridge: 0000:01:02.0
[   20.735114]   IO window: 00003400-000034ff
[   20.735139]   IO window: 00003800-000038ff
[   20.735148]   PREFETCH window: 30000000-31ffffff
[   20.735157]   MEM window: 34000000-35ffffff
[   20.735165] PCI: Bus 6, cardbus bridge: 0000:01:02.1
[   20.735171]   IO window: 00003c00-00003cff
[   20.735179]   IO window: 00001400-000014ff
[   20.735188]   PREFETCH window: 32000000-33ffffff
[   20.735196]   MEM window: 36000000-37ffffff
[   20.735204] PCI: Bridge: 0000:00:1e.0
[   20.735211]   IO window: 3000-3fff
[   20.735221]   MEM window: f4100000-f41fffff
[   20.735230]   PREFETCH window: 30000000-33ffffff
[   20.735253] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.735277] PCI: No IRQ known for interrupt pin A of device 0000:01:02.0.
[   20.735286] PCI: Setting latency timer of device 0000:01:02.0 to 64
[   20.735307] PCI: No IRQ known for interrupt pin B of device 0000:01:02.1.
[   20.735316] PCI: Setting latency timer of device 0000:01:02.1 to 64
[   20.736353] audit: initializing netlink socket (disabled)
[   20.736376] audit(1152652103.758:1): initialized
[   20.736607] VFS: Disk quotas dquot_6.5.1
[   20.736658] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.736796] Initializing Cryptographic API
[   20.736809] io scheduler noop registered
[   20.736827] io scheduler anticipatory registered
[   20.736842] io scheduler deadline registered
[   20.736865] io scheduler cfq registered
[   20.737364] isapnp: Scanning for PnP cards...
[   21.094209] isapnp: No Plug & Play device found
[   21.133120] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   21.134961] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.135171] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.135274] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   21.135453] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.142083] 00:12: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.142382] PCI: Found IRQ 5 for device 0000:00:1f.6
[   21.142404] PCI: Sharing IRQ 5 with 0000:00:1f.3
[   21.142415] PCI: Sharing IRQ 5 with 0000:00:1f.5
[   21.143377] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.143508] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.143519] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.143917] mice: PS/2 mouse device common for all mice
[   21.144326] EISA: Probing bus 0 at eisa.0
[   21.144345] Cannot allocate resource for EISA slot 1
[   21.144354] Cannot allocate resource for EISA slot 2
[   21.144360] Cannot allocate resource for EISA slot 3
[   21.144392] EISA: Detected 0 cards.
[   21.144507] NET: Registered protocol family 2
[   21.152879] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   21.153281] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[   21.153538] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[   21.153848] TCP: Hash tables configured (established 16384 bind 16384)
[   21.153856] TCP reno registered
[   21.154105] TCP bic registered
[   21.154138] NET: Registered protocol family 1
[   21.154159] NET: Registered protocol family 8
[   21.154165] NET: Registered protocol family 20
[   21.154225] Using IPI Shortcut mode
[   21.154335] Freeing unused kernel memory: 288k freed
[   21.174792] input: AT Translated Set 2 keyboard as /class/input/input0
[   21.292250] vga16fb: initializing
[   21.292267] vga16fb: mapped to 0xc00a0000
[   21.410028] Console: switching to colour frame buffer device 80x30
[   21.410046] fb0: VGA16 VGA frame buffer device
[   22.524654] Capability LSM initialized
[   23.885110] ICH2M: IDE controller at PCI slot 0000:00:1f.1
[   23.885146] ICH2M: chipset revision 3
[   23.885153] ICH2M: not 100% native mode: will probe irqs later
[   23.885178]     ide0: BM-DMA at 0x1800-0x1807, BIOS settings: hda:DMA, hdb:pio
[   23.885211]     ide1: BM-DMA at 0x1808-0x180f, BIOS settings: hdc:DMA, hdd:pio
[   23.885270] Probing IDE interface ide0...
[   24.149142] hda: FUJITSU MHM2200AT, ATA DISK drive
[   24.761731] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   24.762101] Probing IDE interface ide1...
[   25.432955] hdc: UJDA710, ATAPI CD/DVD-ROM drive
[   26.044940] ide1 at 0x170-0x177,0x376 on irq 15
[   26.062084] hda: max request size: 128KiB
[   26.142961] hda: 39070080 sectors (20003 MB) w/2048KiB Cache, CHS=38760/16/63, UDMA(66)
[   26.142982] hda: cache flushes not supported
[   26.143382]  hda: hda1 hda2 hda3
[   26.177088] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   26.177140] Uniform CD-ROM driver Revision: 3.20
[   26.963925] usbcore: registered new driver usbfs
[   26.964840] usbcore: registered new driver hub
[   26.970462] USB Universal Host Controller Interface driver v2.3
[   26.971353] PCI: Found IRQ 9 for device 0000:00:1f.2
[   26.971443] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   26.971453] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   26.972491] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   26.972519] uhci_hcd 0000:00:1f.2: irq 9, io base 0x00001820
[   26.973301] hub 1-0:1.0: USB hub found
[   26.973332] hub 1-0:1.0: 2 ports detected
[   26.977581] ieee1394: Initialized config rom entry `ip1394'
[   27.073712] PCI: Found IRQ 11 for device 0000:00:1f.4
[   27.073766] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   27.073775] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   27.074016] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   27.074040] uhci_hcd 0000:00:1f.4: irq 11, io base 0x00002400
[   27.074650] hub 2-0:1.0: USB hub found
[   27.074677] hub 2-0:1.0: 2 ports detected
[   27.178665] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[   27.178700] PCI: Enabling device 0000:01:00.0 (0110 -> 0112)
[   27.178715] PCI: No IRQ known for interrupt pin A of device 0000:01:00.0.
[   27.230024] ohci1394: Failed to allocate shared interrupt 0
[   27.230109] ohci1394: probe of 0000:01:00.0 failed with error -12
[   27.452644] Attempting manual resume
[   27.527217] EXT3-fs: mounted filesystem with ordered data mode.
[   27.565682] kjournald starting.  Commit interval 5 seconds
[   48.210196] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   48.219963] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.266950] hw_random hardware driver 1.0.0 loaded
[   48.285626] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   48.325608] Linux agpgart interface v0.101 (c) Dave Jones
[   48.360814] agpgart: Detected an Intel i815 Chipset.
[   48.366525] agpgart: detected 4MB dedicated video ram.
[   48.373499] agpgart: AGP aperture is 64M @ 0xf8000000
[   49.608888] PCI: Found IRQ 5 for device 0000:00:1f.5
[   49.608915] PCI: Sharing IRQ 5 with 0000:00:1f.3
[   49.608927] PCI: Sharing IRQ 5 with 0000:00:1f.6
[   49.608982] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   49.779020] Real Time Clock Driver v1.12
[   49.790241] input: PC Speaker as /class/input/input1
[   50.031930] input: PS/2 Mouse as /class/input/input2
[   50.048679] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[   50.198286] intel8x0_measure_ac97_clock: measured 79487 usecs
[   50.198298] intel8x0: clocking to 48000
[   50.201409] PCI: No IRQ known for interrupt pin A of device 0000:01:02.0.
[   50.201442] Yenta: CardBus bridge found at 0000:01:02.0 [104d:80df]
[   50.201471] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[   50.201475] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[   50.323526] Yenta: ISA IRQ mask 0x0098, PCI irq 0
[   50.323540] Socket status: 30000006
[   50.323548] Yenta: Raising subordinate bus# of parent bus (#01) from #01 to #05
[   50.323563] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   50.323574] cs: IO port probe 0x3000-0x3fff: clean.
[   50.324164] pcmcia: parent PCI bridge Memory window: 0xf4100000 - 0xf41fffff
[   50.324173] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   50.375212] PCI: No IRQ known for interrupt pin B of device 0000:01:02.1.
[   50.375248] Yenta: CardBus bridge found at 0000:01:02.1 [104d:80df]
[   50.375275] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[   50.375280] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[   50.497369] Yenta: ISA IRQ mask 0x0098, PCI irq 0
[   50.497382] Socket status: 30000006
[   50.497390] Yenta: Raising subordinate bus# of parent bus (#01) from #05 to #09
[   50.497405] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   50.497415] cs: IO port probe 0x3000-0x3fff: clean.
[   50.498001] pcmcia: parent PCI bridge Memory window: 0xf4100000 - 0xf41fffff
[   50.498010] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[   50.773071] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[   50.773085] e100: Copyright(c) 1999-2005 Intel Corporation
[   50.773188] PCI: Enabling device 0000:01:08.0 (0110 -> 0113)
[   50.773205] PCI: Found IRQ 9 for device 0000:01:08.0
[   50.797447] e100: eth0: e100_probe: addr 0xf4105000, irq 9, MAC addr 08:00:46:14:5C:FF
[   51.844791] cs: IO port probe 0x100-0x3af: excluding 0x378-0x37f
[   51.846681] cs: IO port probe 0x3e0-0x4ff: clean.
[   51.847462] cs: IO port probe 0x820-0x8ff: clean.
[   51.848150] cs: IO port probe 0xc00-0xcf7: clean.
[   51.849076] cs: IO port probe 0xa00-0xaff: clean.
[   51.851638] cs: IO port probe 0x100-0x3af: excluding 0x378-0x37f
[   51.853507] cs: IO port probe 0x3e0-0x4ff: clean.
[   51.854302] cs: IO port probe 0x820-0x8ff: clean.
[   51.854989] cs: IO port probe 0xc00-0xcf7: clean.
[   51.855917] cs: IO port probe 0xa00-0xaff: clean.
[   52.240978] Floppy drive(s): fd0 is 1.44M
[   52.255885] FDC 0 is a post-1991 82077
[   52.397079] ts: Compaq touchscreen protocol output
[   52.468949] parport: PnPBIOS parport detected.
[   52.469125] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   52.775901] e100: eth0: e100_watchdog: link up, 10Mbps, half-duplex
[   53.916045] NET: Registered protocol family 17
[   54.187448] lp0: using parport0 (interrupt-driven).
[   54.487497] SCSI subsystem initialized
[   54.577887] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[   54.577902] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   54.577909] ieee1394: sbp2: Try serialize_io=0 for better performance
[   54.752986] Adding 995708k swap on /dev/hda3.  Priority:-1 extents:1 across:995708k
[   54.912534] EXT3 FS on hda2, internal journal
[   55.276228] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   55.276242] md: bitmap version 4.39
[   56.206289] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[   61.489580] NET: Registered protocol family 10
[   61.489904] lo: Disabled Privacy Extensions
[   61.490272] IPv6 over IPv4 tunneling driver
[   71.860147] eth0: no IPv6 routers present
[   96.880609] ppdev: user-space parallel port driver
[   97.573570] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   98.872607] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[   98.872629] hdc: drive_cmd: error=0x04 { AbortedCommand }
[   98.872637] ide: failed opcode was: 0xec
[  102.615842] input: Sony Vaio Jogdial as /class/input/input4
[  102.620705] input: Sony Vaio Keys as /class/input/input5
[  102.623661] sonypi: Sony Programmable I/O Controller Driverv1.26.
[  102.624658] sonypi: detected type2 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = off
[  102.626098] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[  102.626838] sonypi: device allocated minor is 62
[  103.420219] Bluetooth: Core ver 2.8
[  103.420238] NET: Registered protocol family 31
[  103.420244] Bluetooth: HCI device and connection manager initialized
[  103.420271] Bluetooth: HCI socket layer initialized
[  103.506025] Bluetooth: L2CAP ver 2.8
[  103.506042] Bluetooth: L2CAP socket layer initialized
[  103.561449] Bluetooth: RFCOMM socket layer initialized
[  103.561491] Bluetooth: RFCOMM TTY layer initialized
[  103.561496] Bluetooth: RFCOMM ver 1.7
[ 1966.995542] cs: pcmcia_socket0: cardbus cards are not supported.
[ 3207.968669] usb 1-2: new low speed USB device using uhci_hcd and address 2
[ 3208.505917] usbcore: registered new driver hiddev
[ 3208.528956] input: KYE Genius USB Wheel Mouse as /class/input/input6
[ 3208.530542] input: USB HID v1.00 Mouse [KYE Genius USB Wheel Mouse] on usb-0000:00:1f.2-2
[ 3208.531137] usbcore: registered new driver usbhid
[ 3208.531438] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[12659.879816] usb 1-2: USB disconnect, address 2
[12672.710693] e100: eth0: e100_watchdog: link down
[32319.959916] e100: eth0: e100_watchdog: link up, 10Mbps, half-duplex
[32374.491052] ADDRCONF(NETDEV_UP): eth0: link is not ready
[32374.491653] e100: eth0: e100_watchdog: link up, 10Mbps, half-duplex
[32374.493195] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[40473.177167] eth0: no IPv6 routers present
[40953.164451] cs: pcmcia_socket0: cardbus cards are not supported.
[41023.266398] pcmcia: Detected deprecated PCMCIA ioctl usage.
[41023.266420] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[41023.266432] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.

```

---

### Post by funky_munky on 2006-07-12
I will try to see if there is a bios update tonight as well thanks for the help.

---

### Post by Eversmann on 2006-07-12
Try to boot with "lapic" on the kernel to enable local apic. Maybe it helps too ;-)

if there's a bios update, it should resolve the problem of course, allowing you to boot with ACPI enabled. 

And yes, i think the same. acpi is the problem, not having it results in no irq assignment and problem with the resources.

---

### Post by funky_munky on 2006-07-12
> **Ramses said:**
> You could check if there is bios update for your laptop. Read bios-portion [here]("http://winterwolf.co.uk/vaiopm").

Ok I am hacking with Ramses!

I am typing this with my wireless netgear card.  The solution was to upgrade my bios.  Good call Ramses!  If you PM me with your paypal info I can give you the $50 US reward.

I have been trying to figure this out for a while and I only get so much time to try to figure it out so I really apreciate the help.  As far as I am concerned the time I saved was worth more than $50.

Eversmann, thanks so much for your help.  If I had more money I would pay you as well for haning in there with me and being quick to respond.  But I said I would give the money to he who led me to the conclusion and Ramses did that.  I can offer you my thanks though, so again THANK YOU!


P.S. anyone reading this to help with their problems might want to know that I did indeed need pci=biosirq and once I updated the bios I can now boot with acpi=on and klaptop now works and I can change the brightness on my screen.  Suspend to ram does not work but I don't care.  Hibernate works but it is almost as slow as a normal shutdown and bootup so its useless.  But I do not use either of those function in windows either.  I simply wanted my pcmcia netgear card to work and it does!!!!

---

### Post by Eversmann on 2006-07-13
No problem. I thought about the bios update when you said you had irq problems, but the mate said it first.

Anyway, i don't help because the money. I help because people on the forum help each other. That's the spirit of ubuntu, and i won't use it if wouldn't be this way. 

Now you should open a page on [http://wiki.ubuntu.com/LaptopTestingTeam](http://wiki.ubuntu.com/LaptopTestingTeam) and let other people have information about ubuntu on your laptop.

Regards.

---

### Post by funky_munky on 2006-07-13
Hey Ramses where di you go! 

I owe you some money.

---

### Post by yurtboy on 2006-07-14
Did you get it working?
Not only would the 50 be nice but I need to set this up for a client

---

### Post by funky_munky on 2006-07-15
Yes it is working and I still have not paid Ramses because he is not responding.

Ramses, if you are listening I owe you the $50 US bounty.  Please respond.  I would like to pay it before I end up spending it!

---

### Post by funky_munky on 2006-07-15
HOw do you edit a thread title so that I can put SOLVED on the title?

---

### Post by funky_munky on 2006-07-18
I guess I will have to put a time limit on collecting the bounty or this could be hanging for a long time.

If anyone thinks its rude of me to put a time limit on collecting the money after the fact please tell that it is rude.

I want to pay and get this over with but I need to pay it while I still have the money.

Ramses where are you?  I sent a PM and I am listening here.

Unless others on the forum say otherwise I think that I will have to say if you don't contact me within 2 weeks (post here so its public record) then the bounty will disappear.  That puts us at August 1st 2006.  Please contact me here by that date.

---

### Post by shortbus on 2006-07-18
> **funky_munky said:**
> Hey Ramses where di you go! 

I owe you some money.

Send him a PM so he knows to get a hold of you.;)

---

### Post by funky_munky on 2006-07-18
already did that on day one!

This guy just dropped off the face of the earth.

I would email him but he blocked that in these forums.

---

