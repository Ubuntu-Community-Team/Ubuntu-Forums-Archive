---
title: "Ubuntu 14.04 completely freezes"
date: 2014-12-18
forum: Hardware
---

### Post by sgiannop on 2014-12-18
Hello everyone. I recently managed to repair an old desktop computer with several problems. Now i have ubuntu 14.04 installed and running on it.
I use to boot at tty and startx when i please, and i use gnome 3 fallback by default. The problem is a complete system freeze at random times. The mouse
cursor doesn't move the keyboard doesn't respond, and the following combinations:

Alt+Ctrl+F1-F6
Alt+Ctrl+Backspace
Alt+SysRq+REISUB

do nothing

The only solution is hard reset. The problem isn't really random, as it almost certainly appears (at least) in the following occasions:

[LIST=1]
[*]    When i use for a couple of minutes the synaptic package manager, especially when i use the scrollbar. 
[*]    When i use firefox, especially when i use the scrollbar. 
[/LIST]

I have no problem using tty1 as long as the resolution is 640x480 (which is the default). If i change it in /etc/default/grub:

```

GRUB_CMDLINE_LINUX_DEFAULT="text vga=791"

```

then the computer freezes in tty1 as well. Specifically

[LIST=1]
[*]     When i use tty1, before i start the x server 
[*]     When i logout to tty1. 
[/LIST]

My computer has the following hardware:

```

sudo lshw

```

```

socrates
    description: Computer
    product: 775Dual-880Pro
    version: 1.00
    serial: 00000000
    width: 64 bits
    capabilities: smbios-2.3 dmi-2.3 vsyscall32
    configuration: uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: 775Dual-880Pro
       physical id: 0
       version: 1.00
       serial: 00000000
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.70
          date: 10/04/2007
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 3
          bus info: cpu@0
          version: Intel(R) Pentium(R) 4 CPU 3.00GHz (64bit supported
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          size: 3GHz
          capacity: 3GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl est cid cx16 xtpr cpufreq
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 1497MiB
     *-pci:0
          description: Host bridge
          product: PT880 Ultra/PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:f8000000-fbffffff
        *-generic UNCLAIMED
             description: PIC
             product: PT894 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: PT890 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:64 ioport:1000(size=4096) memory:d5e00000-dfefffff memory:b5d00000-d5cfffff
           *-display
                description: VGA compatible controller
                product: NV43 [GeForce 6600 LE]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:24 memory:d8000000-dbffffff memory:c0000000-cfffffff memory:de000000-deffffff memory:dfee0000-dfefffff
        *-multimedia:0
             description: Multimedia video controller
             product: Bt878 Video Capture
             vendor: Brooktree Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: vpd pm bus_master cap_list
             configuration: driver=bttv latency=32 maxlatency=40 mingnt=16
             resources: irq:18 memory:d5dff000-d5dfffff
        *-multimedia:1 UNCLAIMED
             description: Multimedia controller
             product: Bt878 Audio Capture
             vendor: Brooktree Corporation
             physical id: a.1
             bus info: pci@0000:00:0a.1
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: vpd pm bus_master cap_list
             configuration: latency=32 maxlatency=255 mingnt=4
             resources: memory:d5dfe000-d5dfefff
        *-storage
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm bus_master cap_list
             configuration: driver=sata_via latency=32
             resources: irq:20 ioport:ec00(size=8) ioport:e880(size=4) ioport:e800(size=8) ioport:e480(size=4) ioport:e400(size=16) ioport:e000(size=256)
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=32
             resources: irq:20 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fc00(size=16)
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:dc00(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d080(size=32)
        *-usb:2
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:d000(size=32)
        *-usb:3
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:21 ioport:ef00(size=32)
        *-usb:4
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:21 memory:dffff800-dffff8ff
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia:2
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=snd_via82xx latency=0
             resources: irq:22 ioport:d400(size=256)
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:13:8f:6f:30:9f
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full ip=192.168.1.2 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             resources: irq:23 ioport:d800(size=256) memory:dffffc00-dffffcff
     *-pci:1
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: PT890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: PT894 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD400BB-32CX
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 02.0
             serial: WD-WMAC51112954
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0001d033
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: e2d10652-ea50-45ec-9d01-307fa01b7bc8
                size: 36GiB
                capacity: 36GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-10-20 07:01:56 filesystem=ext4 lastmountpoint=/ modified=2014-12-18 11:16:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-12-18 11:16:49 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 972MiB
                capacity: 972MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 972MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 4
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD DD DW1640
             vendor: BENQ
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: BSLB
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=open

```

I recently updated bios to the last available version (P1.70, as stated in the above list), but it didn't change something.
I tend to believe this is a graphics adapter problem (though i am not sure at all). This is Geforce 6600 LE, and the driver is nvidia-304.125, which is the most updated.
I have this problem almost six months, and i have tried at least the last three driver versions, which have exactly the same problem (versions 304.88 and 304.40).
It seems not a problem of a specific desktop manager as it appears in lxde as well.

The file /var/log/mcelog after each reset reports:

```

Hardware event. This is not a software error.
MCE 0
CPU 0 BANK 0 
TIME 1418822692 Wed Dec 17 15:24:52 2014
MCG status:
MCi status:
Uncorrected error
Processor context corrupt
MCA: Internal Timer error
STATUS a20000008c010400 MCGSTATUS 0
MCGCAP 180204 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 15 Model 4

```

Any ideas?

---

### Post by mörgæs on 2014-12-18
Thanks for a post with a lot of useful details. Not all posts are like this.

Have you checked the processor using this tool? 
[http://www.intel.com/support/processors/sb/CS-031726.htm](http://www.intel.com/support/processors/sb/CS-031726.htm)

---

### Post by sgiannop on 2014-12-19
Thanks a lot for the reply. I tried what you propose, but unfortunately i  couldn't install IPDT tool in my Fedora USBFlash Live OS, because  exactly the same problem appears. Computer freezes completely a few  minutes after i manage to start windows manager (xfce4 in Fedora). Seems  worse than i thought. I 'll try it more times and i 'll post the  results. Nevertheless, it seems quite possible to be a CPU problem. I  'll try to find another CPU and give it a try. That's something i  haven't tried yet.

---

### Post by sgiannop on 2014-12-19
Hello guys. Finally after months i solved my problem easily and 100%. It was a BIOS setting. I entered BIOS during boot and i set my CPU, NOT to be controlled
by operating system, but from BIOS instead. Everything works perfect now. Random freezes totally disappeared. ;)

---

### Post by valeriancafe on 2014-12-30
I have tried Debian, Ubuntu 14.04 64 bit, Fedora 21 all freezing I have a Nvidia 210 card , ASUS E45M1-I DELUXE motherboard , sata hdd GPT formatted, I looked in the bios to find this setting it's not their  Bios version ASUS EFI 0504 CPU amd e-450 :confused:](*,) I am forced to install ubuntu 12.04 LTS and install Nvidia driver it's working :shock: It froze again :(

---

