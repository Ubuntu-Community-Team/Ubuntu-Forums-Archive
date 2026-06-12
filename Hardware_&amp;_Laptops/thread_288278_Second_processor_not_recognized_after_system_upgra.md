---
title: "Second processor not recognized after system upgrade"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by Gustavo Narea on 2006-10-29
Hello.

I was using Kubuntu Dapper and my two processors were working fine, but after I upgraded my system to Edgy, there's only one of them recognized:

```
gustavo@valencia:~$ sudo cat /proc/cpuinfo
Password:
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up pni monitor vmx est tm2 xtpr
bogomips        : 3667.50
```

I'm using a Dell Inspiron 6400 and linux-686-smp is already installed.

TIA.

Cheers!

---

### Post by jinx099 on 2006-10-29
I'm having problems with my Core 2 Duo and Edgy as well.  I have 2 kernels installed, the standard i386 kernel and the generic kernel.  SMP is supported on the generic kernel but not the i386 kernel.  What is the output of "uname -a"?  

Only 1 core on my system is detected on the i386 kernel and the speed is right, but on the generic kernel the speed is wrong but both cores are detected.  AFAIK the linux-686-smp kernel you mentioned that was used in dapper no longer applies to edgy and you are supposed to use the generic kernel.

---

### Post by John.Michael.Kane on 2006-10-29
Have you both tried doing non-dist-upgrade installs ie: clean installs?

Also you should include your full system specs when seeking help.

---

### Post by Old Pink on 2006-10-29
> **Gustavo Narea said:**
> ```

model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
```
Your 1.83Ghz processor is running at only 1Ghz? :confused:

---

### Post by jinx099 on 2006-10-29
I'm running edgy from a clean install.  Check out my thread on the issue:  [http://www.ubuntuforums.org/showthread.php?t=286711](http://www.ubuntuforums.org/showthread.php?t=286711)

---

### Post by Gustavo Narea on 2006-10-30
Hi and thank you all for your answers.

> **jinx099 said:**
> What is the output of "uname -a"?

```
gustavo@valencia:~$ uname -a
Linux valencia 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux
```

> **SD-Plissken said:**
> Have you both tried doing non-dist-upgrade installs ie: clean installs?

Unfortunately, I don't have enough time to do so this week.

> **SD-Plissken said:**
> Also you should include your full system specs when seeking help.

Oops. Sorry.

```
gustavo@valencia:~$ sudo lshw
Password:
valencia
    description: Portable Computer
    product: MM061
    vendor: Dell Inc.
    serial: H15QMB1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-3100-1035-8051-C8C04F4D4231
  *-core
       description: Motherboard
       product: 0KD882
       vendor: Dell Inc.
       physical id: 0
       serial: .H15QMB1.CN486436787979.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A06 (06/09/2006)
          size: 64KB
          capacity: 512KB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU           T2400  @ 1.83GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: Microprocessor
          size: 1833MHz
          capacity: 1833MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up pni monitor vmx est tm2 xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KB
             capacity: 8KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MB
             capacity: 2MB
             clock: 66MHz (15ns)
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: 7F7F7F7F7F510000
             physical id: 0
             serial: 0308B510
             slot: DIMM_B
             size: 256MB
             width: 64 bits
             clock: 533MHz (1.87617ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: 7F7F7F7F7F510000
             physical id: 1
             serial: 0308B917
             slot: DIMM_A
             size: 256MB
             width: 64 bits
             clock: 533MHz (1.87617ns)
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:dff00000-dff7ffff ioport:eff8-efff iomemory:c0000000-cfffffff iomemory:dfec0000-dfefffff irq:169
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:dff80000-dfffffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:dfebc000-dfebffff irq:225
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Network controller
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0b:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:dfdfc000-dfdfffff irq:4
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf80-bf9f irq:217
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf60-bf7f irq:225
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-386 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf40-bf5f irq:233
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-386 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: USB MOUSE
                   vendor: KYE
                   physical id: 1
                   bus info: usb@3:1
                   version: 0.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf20-bf3f irq:50
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-10-386 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:ffa80000-ffa803ff irq:217
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-10-386 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@03:00.0
                logical name: eth0
                version: 02
                serial: 00:15:c5:a7:f0:19
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=full ip=192.168.1.33 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: iomemory:df9fe000-df9fffff irq:209
           *-firewire
                description: FireWire (IEEE 1394)
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@03:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:df9fd800-df9fdfff irq:177
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@03:01.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci
                resources: iomemory:df9fd400-df9fd4ff irq:58
           *-system:1 UNCLAIMED
                description: System peripheral
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@03:01.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:df9fd500-df9fd5ff irq:11
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@03:01.3
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:df9fd600-df9fd6ff irq:11
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.4
                bus info: pci@03:01.4
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:df9fd700-df9fd7ff irq:11
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix
             resources: ioport:bfa0-bfaf irq:209
           *-disk
                description: SCSI Disk
                product: Hitachi HTS54106
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MB3O
                serial: MPBCP0XGJYWYNM
                size: 54GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 53GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 1451MB
                   capabilities: extended partitioned partitioned:extended
           *-cdrom UNCLAIMED
                description: SCSI CD-ROM
                product: DVD+-RW DW-Q58A
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.0.0
                version: UDS2
                capabilities: removable
                configuration: ansiversion=5
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             resources: ioport:10c0-10df irq:4
  *-battery
       product: DELLUD26568
       vendor: SMP
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 48000mWh
       configuration: voltage=11.1V
```

> **jinx099 said:**
> I'm running edgy from a clean install.  Check out my thread on the issue:  [http://www.ubuntuforums.org/showthread.php?t=286711](http://www.ubuntuforums.org/showthread.php?t=286711)

Thank you, jinx099: I'm now subscribed to that thread in case someone finds the solution for the speed problem.

----

What should I do now? ](*,) 

TIA.

---

### Post by jinx099 on 2006-10-30
You need to install the generic kernel, the i386 kernel does not support SMP which is required to use both cores.  Type this:

```
sudo apt-get install linux-image-generic
```

Then reboot and select the generic kernel in the grub menu.

---

### Post by Gustavo Narea on 2006-10-31
Hi!

> **jinx099 said:**
> You need to install the generic kernel, the i386 kernel does not support SMP which is required to use both cores.  Type this:

```
sudo apt-get install linux-image-generic
```

Then reboot and select the generic kernel in the grub menu.

It was installed and now I'm using my generic kernel with my two processors! Thank you!

Anyways, is this right?...

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3667.69

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3662.25
```

I don't understand that output very well...

TIA.

---

### Post by John.Michael.Kane on 2006-10-31
Gustavo Narea Yes it's right 
processor       : 0 = core 1
processor       : 1 = core 2

It would also seem speed step is working as well that would explain your cpu reading @ 1000.000 once your put the machine under heavy load you should see an increase.

---

### Post by Gustavo Narea on 2006-11-01
Hi!

> **SD-Plissken said:**
> Gustavo Narea Yes it's right 
processor       : 0 = core 1
processor       : 1 = core 2

Thanks!

> **SD-Plissken said:**
> It would also seem speed step is working as well that would explain your cpu reading @ 1000.000 once your put the machine under heavy load you should see an increase.

Yes, you're right! So, I guess it's not something to worry of...

Thanks once again!

---

