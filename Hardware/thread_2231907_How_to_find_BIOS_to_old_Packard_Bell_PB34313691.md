---
title: "How to find BIOS to old Packard Bell PB34313691"
date: 2014-06-28
forum: Hardware
---

### Post by Azyx on 2014-06-28
I have upgraded the CPU from Sempron 3400+ to an Athlon 64 6000+ so I think I need a new BIOS? Now Ubuntu 12.04.3 halt with a light purple sceen and nothing happend. I can go in in BIOS and so and it find the processor, but it's unknown, but clockspeed are right, I think 3.0GHz.

I Have tried to go to Parkard Bell, but I can not find the computer on there site, test brows and search for S/N number. Does not exist on that site. Think they have not older stuff there. 

The motherboard are an ASUS N2M-NVM/S . I does not exist on ASUS, but there are several N2M-NVM, but not one with the same configuration (Mine have only 2 PCI-slots, 1 mini PCIe and one PCIe) and it also only have 2 SATA connectors, compared to M2N. [http://www.asus.com/Motherboards/M2N/HelpDesk/](http://www.asus.com/Motherboards/M2N/HelpDesk/)

Boot screen
06/01/2006-C51-MCP51-M2N-NVM-00

Back on the computer.
Model/Type ref UTOW-AUC
MS WHQL N AUC00 AD0067

S/N 113172660306
P/N PB34313691

Does someone know how I can find BIOS and manual for BIOS? Is it possible to the Ubuntu 12.04.3 boot on another way? Like safe boot or something?

Thanks for all help

/Cheers

---

### Post by oCyiIsejN9jk on 2014-06-28
Hi, does using "nomodeset" help at all?

---

### Post by Azyx on 2014-06-28
How do I do that?

---

### Post by Vladlenin5000 on 2014-06-28
Forget about 'nomodeset' (totally unrelated) and forget about any new BIOS version. Your new processor simply isn't supported in that board, no matter what.

---

### Post by Azyx on 2014-06-28
Normally new BIOS support newerprocessors.  Why not with this motherboard?

---

### Post by mörgæs on 2014-06-28
Azyx, please tell exactly all the steps that happens before the purple screen.

---

### Post by Vladlenin5000 on 2014-06-28
> **Azyx said:**
> Normally new BIOS support newerprocessors.  Why not with this motherboard?

Because yours is an OEM product made for PB. That's why you couldn't find it either at the (real) manufacturer's website. BIOS updates for PB product's (or for almost all brand name computers) are intended to correct issues, improve stability, etc. but not to support new CPUs. The logic is if you want a better processor PB is happy to sell you a brand new computer. You aren't supposed to replace parts like you do with your own builds with generic motherboards and stuff.

---

### Post by Azyx on 2014-06-28
1) Bios-boot (mem-test and hardware-list), 2) Purple screen, 3) "Ubuntu ...."-screen, darker, and flickering screen (flash in white, when moving mouse). After a while, maybe not purple, just very dark screen and no response. I can go to terminal, with Ctrl + Alt + F1 :)

---

### Post by Vladlenin5000 on 2014-06-28
You're wasting your time... Sorry, but it's the truth.
You already know it isn't supported because > it find the processor, but it's **unknown**.
Even if you can find a new BIOS version and update it successfully the chances to get the new processor recognized are virtually zero.

---

### Post by mörgæs on 2014-06-28
The processor obviously works on the motherboard, as first part of the boot proceeds normally. Did you try nomodeset as suggested above?

---

### Post by Azyx on 2014-06-29
Not yet. Haven't find how I shall do, but I get into the terminal now. Have installed sshd on the machine.

edit. [http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

---

### Post by Azyx on 2014-06-29
I edit grub config file by adding [FONT=arial black][COLOR=#008000]nomodese [FONT=arial][/FONT][/COLOR][FONT=arial]after "quiet splash" in the config file. I sudo update-grub afterward. Screen is still black. ssh work.[/FONT][/FONT]

sudo nano /etc/default/grub

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [FONT=arial black][COLOR=#008000]nomodese[/COLOR][/FONT]t"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)

---

### Post by mörgæs on 2014-06-29
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Azyx on 2014-06-29
Here is the outcome of sudo lshw -sanitize

```
@Packard:~$ sudo lshw -sanitize
[sudo] password for a: 
computer                  
    description: Desktop Computer
    product: IMELIA 2415
    vendor: PACKARD BELL BV
    version: PB34313691
    serial: [REMOVED]
    width: 64 bits
    capabilities: vsyscall32
    configuration: boot=normal chassis=desktop uuid=[REMOVED]
  *-core
       description: Motherboard
       product: M2N-NVM
       vendor: Packard Bell BV
       physical id: 0
       version: 1.XX
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: M2N-NVM 0301
          date: 06/01/2006
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: AMD Processor model unknown
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 1
          bus info: cpu@0
          version: AMD Processor model unknown
          slot: Socket AM2
          size: 3GHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: d
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-cpu:1
          description: CPU
          vendor: AMD
          physical id: 4
          bus info: cpu@1
          version: AMD Processor model unknown
          slot: Socket AM2
          size: 3GHz
          capacity: 3700MHz
          clock: 200MHz
        *-cache:0
             description: L1 cache
             physical id: c
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: e
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 2e
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 0
             serial: [REMOVED]
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 1
             serial: [REMOVED]
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR2 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 2
             serial: [REMOVED]
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 667 MHz (1.5 ns)
             product: None
             vendor: None
             physical id: 3
             serial: [REMOVED]
             slot: A3
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: NVIDIA Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: NVIDIA Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: NVIDIA Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: NVIDIA Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: NVIDIA Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: NVIDIA Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:e000(size=4096) memory:fd700000-fd7fffff ioport:fde00000(size=1048576)
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 ioport:d000(size=4096) memory:fdd00000-fddfffff ioport:fdc00000(size=1048576)
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42 ioport:b000(size=4096) memory:fd900000-fd9fffff ioport:fd800000(size=1048576)
     *-display
          description: VGA compatible controller
          product: C51 [GeForce 6150 LE]
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:16 memory:fb000000-fbffffff memory:e0000000-efffffff memory:fc000000-fcffffff memory:f4000000-f401ffff
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: NVIDIA Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:7 ioport:4c00(size=64) ioport:4c40(size=64)
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: NVIDIA Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP51 USB Controller
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB controller
          product: MCP51 USB Controller
          vendor: NVIDIA Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02e000-fe02e0ff
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:fd00(size=16)
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:f800(size=16) memory:fe02d000-fe02dfff
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: NVIDIA Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:c000(size=4096) memory:fdb00000-fdbfffff memory:fda00000-fdafffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
             vendor: Texas Instruments
             physical id: 5
             bus info: pci@0000:04:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
             resources: irq:19 memory:fdbff000-fdbff7ff memory:fdbf8000-fdbfbfff
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:23 memory:fe028000-fe02bfff
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: NVIDIA Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth1
          version: a3
          serial: [REMOVED]
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=[REMOVED] latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:20 memory:fe02c000-fe02cfff ioport:f700(size=8)
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: 7
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST340014AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 8.12
             serial: [REMOVED]
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=7f837f83
           *-volume:0
                description: Linux swap volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 1
                serial: [REMOVED]
                size: 3814MiB
                capacity: 3814MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 24GiB
                capacity: 24GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-06-27 13:09:56 filesystem=ext4 lastmountpoint=/ modified=2014-06-27 13:32:08 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-06-29 14:20:09 state=mounted
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 9534MiB
                capacity: 9534MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /home
                   capacity: 9534MiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
     *-scsi:1
          physical id: 8
          bus info: usb@2:7
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde

```

---

### Post by Yellow Pasque on 2014-06-29
I do see a newer BIOS for the board (0501), but the only report I can find of someone trying it with a newer CPU is negative: [http://forums.mydigitallife.info/threads/5863-Award-amp-AMI-Bios-mod-requests?p=655988&viewfull=1#post655988](http://forums.mydigitallife.info/threads/5863-Award-amp-AMI-Bios-mod-requests?p=655988&viewfull=1#post655988)

If I was trying to get an unidentified CPU to run, I would try to disable Cool'n'Quiet and any other extra CPU feature. I would also make sure to manually set the specified voltage.

---

### Post by Azyx on 2014-06-29
I can connect true ctrl + alt + F1 and SSH, so I think there are something wrong with the onboard nvidia gfx? No xorg.conf file either...

---

### Post by Azyx on 2014-06-30
It seems to bee a problem with the onboard gfx. Tested with another PCIe DVI-gfx, and it worked. The card only have DVI-connection and I don't have more than one DVI-monitor. Have seen people have had problem with GeForce 6150 LE and had to install older nvidia-drivers or 'open' drivers. I have forget a lot of commands and stuff. How do I see what drivers in use with terminal?

---

### Post by Bashing-om on 2014-06-30
Azyx; Hello,

Not much help on the main topic of this thread, but I can relate the commands ;
To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```

[INDENT][INDENT]a bit of help, no ?
[/INDENT][/INDENT]

---

### Post by Azyx on 2014-06-30
Bashing-om Thanks :). I find a DVI-VGA adapter and use the PCIE gfx-card now. Going to bee better performance also. /Cheers.

---

### Post by mörgæs on 2014-07-01
Nvidia 6150 appears to be a problem for Ubuntu, at least according to a quick googling. Swapping for another card might be a good idea.

---

### Post by squakie on 2014-07-01
I doubt I'll have more luck than the experts who already posted, but I know I have had motherboards in the past for which the manufacturer specifically released a new bios image to support new CPU's - so it's not unheard of.

---

### Post by squakie on 2014-07-01
I also found 0501, but from a different download than that in the other forum.  Here is one success story, including clock and memory times:

[URL="http://krestenhillerup.dk/andet/computer-tech/"]http://krestenhillerup.dk/andet/computer-tech/
[/URL]
There is a download for the 0501 bios at winbios as well.

Note that the above link also mentions your motherboard, so the update should at least install.

BTW - when you go in to your BIOS, or check the hardware in Ubuntu - do you see the correct number of cores (I would think only 1 since you don't say it's an X2) but the name just shows as unknown?  I've seen BIOS updates before to cover identifying the newer CPU's but I don't know if 0501 would actually fix that id process.

My suggestion:  if you know enough to know how to flash a BIOS I would:

- download the BIOS image - be sure to run a virus/trojan/etc. scanner on the file!
- follow the instructions for building a DOS disk/USB stick to flash the BIOS
- find out if the flash utility will allow backing up your current BIOS image - in your case I would highly recommend backing up what you have first
- flash the BIOS to 0501
- did it help any?  
- did it make things worse?  reflash using the saved old image 

That's just me - I'm not the big-time expert some of these folks are, especially for Ubuntu.  I have done this type of thing literally hundreds of times in the past.[URL="http://krestenhillerup.dk/andet/computer-tech/"]
[/URL]

---

### Post by Azyx on 2014-07-01
[ 						 							]("http://ubuntuforums.org/member.php?u=939075")[**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075")

Yes. I had also that impression. I have a Nvidia 8600 GT, so use that instead. By the way, BIOS does not support my Athlon 64 6000+ processor, but I work. Does it matter for the performace, that BIOS support the processor?

---

### Post by mörgæs on 2014-07-02
The BIOS does support the processor, else your system would show a black screen. It may not support it *officially*, but that's a different matter.

Yes, there could be performance improvements in a new BIOS.

---

### Post by squakie on 2014-07-02
+1.  Indeed it wouldn't run if it couldn't recognize it.  Usually the BIOS updates for new processors really only report the CPU - e.g.,  yours would go from "unknown" to what ever the processor string is from your CPU.

---

### Post by Azyx on 2014-07-02
Thanx[ 						 					]("http://ubuntuforums.org/member.php?u=1741485") 				 				 					 						 	[**[COLOR=#000000]squakie[/COLOR]**]("http://ubuntuforums.org/member.php?u=1741485") :)

No, It's shows 2 core, and have a cpu clockspeed  3GHz :) So It does seems to find parameters for the CPU to bee working at right conditions. Thanx again for the link to new BIOS, but I think I will wait till I find problems with BIOS 0301 from 2006 (Little risk it's going bad, AND if It's not exactly the same hardware there may be problems) /Cheers

---

### Post by Azyx on 2014-07-02
[**[COLOR=#000000]squakie[/COLOR]**]("http://ubuntuforums.org/member.php?u=1741485"). One strange thing is that (s)he with the same motherboard as I, could not run on Athlon X2 64 5000+ at all, but my 6000+ started, just showing 'unknown'. 'Supported' CPU are little strange. Often they made an upgrade of BIOS to se new processors, even If
'unsupported' works, I think.

---

### Post by Azyx on 2014-07-02
Maybe we can say that the motherboard support the CPU, but not BIOS ;) I will wait untill there be a problem cos it is a risk to upgrade and the above found BIOS are not official....

---

### Post by squakie on 2014-07-02
That's what I meant in my last post about the CPU id.  It can determine things like the speed and the number of cores, but trying to read the actual CPU ID (like AMD Athlon X2) fails.  This in no way should affect the performance of your computer - if it know the cores, etc., and your system is running it should work.  I had his problem in a desktop I had several years ago - I think it was an Asus motherboard - and when I upgraded the CPU in it the same thing happened.  Ran fine, no CPU id.  An eventual BIOS update solved the CPU id problem.

---

