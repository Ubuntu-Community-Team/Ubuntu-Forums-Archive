---
title: "pae available, but refuses to boot"
date: 2016-06-04
forum: Hardware
---

### Post by martinr on 2016-06-04
The Xubuntu 16.04 live installation DVD fails to boot with the message:
> This kernel requires the following features not present on the CPU:
pae
Unable to boot - please use a kernel appropriate for your CPU.

But my CPU is a:
[INDENT]Intel Pentium M 735, Dothan, (2MB L2 Cache, 1.70 GHz, 400 MHz FSB)[/INDENT]

When I lookup the [specification on the Intel site]("http://ark.intel.com/products/27588/Intel-Pentium-M-Processor-735-2M-Cache-1_70A-GHz-400-MHz-FSB#@specifications"), then it says:
[INDENT]Physical Address Extensions (PAE) 	32-bit is available[/INDENT]

I can force it to boot with the forcepae boot parameter, but I'm very weary about that and don't want to base my future work on shaky fundamentals.

What is wrong here?

---

### Post by ajgreeny on 2016-06-04
Use a terminal command to double check this before we go any further.
```
cat /proc/cpuinfo | grep pae 
```

---

### Post by martinr on 2016-06-04
The Xubuntu 16.04 live DVD won't boot, so I can't open a terminal. (Chicken and the egg problem, ...) #-o
The Intel specs schow that the processor has **pae** capabilities.
I'll try it with Xubuntu 12.04 later.

---

### Post by ajgreeny on 2016-06-04
OK, sorry about that.  I assumed, wrongly it seems that you were already a ubuntu user of some time as your number of posts is hidden.

Good luck with this; it seems very odd that you get that message if the cpu really is pae enabled.

---

### Post by martinr on 2016-06-04
Here is the output:
```

# cat /proc/cpuinfo | grep pae
# 

```
It's a bit disappointing. Nothing :(

I added this for reference:
```

# cat /proc/cpuinfo | grep -i flags
flags           : fpu vme de pse tsc msr mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2

```

So /proc/cpuinfo doesn't show the pae capability for the Intel Pentium M 735, Dothan, but according to the [specs from Intel]("http://ark.intel.com/products/27588/Intel-Pentium-M-Processor-735-2M-Cache-1_70A-GHz-400-MHz-FSB#@specifications"), it certainly does.

Does this mean, that the BIOS doesn't recognise the CPU correctly? I am running the latest BIOS release available (from 2008). Could the package: "intel-microcode" be of help? Is that evaluated before booting?

Where do things go wrong?

---

### Post by sudodus on 2016-06-04
> Intel Pentium M 735, Dothan, (2MB L2 Cache, 1.70 GHz, 400 MHz FSB)

Pentium M with 400 MHz FSB usually have PAE capability but no PAE flag. It is for this very reason, that the forcepae boot option was created. I have the same or very similar CPU in an IBM Thinkpad T42. I have used that computer to test and help develop several new versions of Ubuntu and the operation with forcepae has been very reliable.

See also this link [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by Dennis N on 2016-06-04
My Dell 6000 laptop from 2005 uses Pentium M 730 1.6 gHz, 533 MHz. 

From some notes I made years ago on the Pentium M 700 series, the Pentium M 7XX 533 MHz FSB models released in 2005 have PAE support enabled, but in earlier Pentium M 7XX 400 MHz FSB models from 2004 it is not enabled. Available does not equate to enabled. 

533 MHz models: 730 (1.6 GHz), 740 (1.73 GHz), 750 (1.86 GHz), 760 (2.0 GHz) and 770 (2.13 GHz)

400 MHz models: 710 (1.4 GHz), 715 (1.5 GHz), 725 (1.6 GHz), 735 (1.7 GHz), 740 (1.73 GHz), 745 (1.8 GHz), 750 (1.86 GHz), 755 (2.0 GHz), and 765 (2.1 GHz)

You could verify this. If true, you would need to use the forcepae method.

---

### Post by martinr on 2016-06-04
> **ajgreeny said:**
> OK, sorry about that.  I assumed, wrongly it seems that you were already a ubuntu user of some time as your number of posts is hidden.

Good luck with this; it seems very odd that you get that message if the cpu really is pae enabled.
No worries. I've been a *nix user for a long time. :D
I had to screw open my laptop in order to find out the S-spec number on the CPU. \\:D/
So I was operating from a desktop machine running an ahum cloudy operating system. 
But I posted the result that I found with Xubuntu 12.04 above.

> **Dennis N said:**
> Available does not equate to enabled. 

What does that mean?
The [Intel specs]("http://ark.intel.com/products/27588/Intel-Pentium-M-Processor-735-2M-Cache-1_70A-GHz-400-MHz-FSB#@specifications") show that it has the feature. I don't think they could get away with marketing a feature that turns out to be disabled? :confused:

---

### Post by sudodus on 2016-06-04
I'm fine running with forcepae. If you are not, you can try Debian, ToriOS, Puppy Linux or Tiny Core. (Debian provides 32-bit versions with and without PAE, so you should choose the correct iso file.)

---

### Post by martinr on 2016-06-04
> **sudodus said:**
> Pentium M with 400 MHz FSB usually have PAE capability but no PAE flag. It is for this very reason, that the forcepae boot option was created. 
Okay, if the processor has the feature, why not just add the flag to advertise it then?
Did somebody make a mistake? Can't that be fixed instead of the whole world having to go on a wild goose chase, revisit the problem and work around it?
> **sudodus said:**
> 
See also this link [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)
I read this first before making this post, but it only speaks of a problem with the Banias family of processors. Mine is from the Dothan family. The article that you referenced says:
> Pentium M's of the Dothan family display the PAE flag correctly and support the latest Buntus without modifications. The same distinction (Banias versus Dothan) goes for the lower performing Celeron M processors. 

---

### Post by sudodus on 2016-06-04
> **martinr said:**
> Okay, if the processor has the feature, why not just add the flag to advertise it then?

We are talking about approx. 12 year old hardware. Who in the commercial world cares ;-)

---

### Post by martinr on 2016-06-04
> **sudodus said:**
> I'm fine running with forcepae. If you are not, you can try Debian, ToriOS, Puppy Linux or Tiny Core. (Debian provides 32-bit versions with and without PAE, so you should choose the correct iso file.)
Thanks for your reply, but I'm trying to understand what goes wrong here and why the pae flag is not set? It seems to be very intentional.

One would reckon that problems would have been fixed by then, especially when the previous flavours of Ubuntu (6,8,10 and 12) all ran without any pae problems and I've especially chosen for **X**ubuntu because its a little older. (It's 10 year old not 12) If the software has a melt down I still have a big problem. I'd rather know in advance.

---

### Post by sudodus on 2016-06-04
Ubuntu provided a non-pae kernel until (and including) 12.04.1 LTS (the precise kernel). After that Ubuntu provided only a 32-bit PAE kernel and a 64-bit kernel. People were using fake-pae with 12.10, 13.04 and 13.10 to run your kind of CPUs, Celeron M and Pentium M of that age. The boot option forcepae was introduced with 14.04 LTS (and the trusty kernel).

If you want to feel safe, please use a linux distro with a non-pae kernel.

---

### Post by martinr on 2016-06-04
Why can't the pae flag be added for the specific Pentium M CPUs that support pae?
Where does the flag come from?
Who maintains it?

---

### Post by sudodus on 2016-06-04
If a CPU has PAE capability, the flag *should* be provided by the CPU hardware, but is not (for this particular piece of hardware). Someone has made it publicly known that the capability is there, so the software can 'cheat' by providing the flag, or if you wish, 'pretending' that there is a hardware flag, and that way allow PAE software to be used when it detects this CPU hardware.

Some details are described at the following wikipedia link,

[https://en.wikipedia.org/wiki/Pentium_M](https://en.wikipedia.org/wiki/Pentium_M)

> Revisions of the Dothan core were released in the first quarter of 2005 with the Sonoma chipsets and supported a 533 MT/s FSB and XD (Intel's name for the NX bit) (and PAE support required for it was enabled, unlike earlier Pentium Ms that had it disabled). These processors include the 730 (1.6 GHz), 740 (1.73 GHz), 750 (1.86 GHz), 760 (2.0 GHz) and 770 (2.13 GHz).

We can only guess why earlier Pentium Ms had PAE support disabled (I guess they mean the PAE flag).

---

### Post by martinr on 2016-06-05
> **sudodus said:**
> 
We can only guess why earlier Pentium Ms had PAE support disabled (I guess they mean the PAE flag).


I was already two steps ahead of you, when I opened this post. I'll deep dive, hopefully you can follow.

I suppose that the PAE flag is handed down from the BIOS to the bootloader and won't contain fixes since the most actual BIOS from 2008. Then there's the latest (Date: 11/9/2015) [Linux Processor Microcode Data File from Intel]("https://downloadcenter.intel.com/download/25512/Linux-Processor-Microcode-Data-File"). The newest 735 definitions are contained in that file. I'm not sure if the new Linux Processor Microcode Data File takes care of the PAE flag though. Furthermore I'm not sure if that data file can be made effective **at boot time** (overruling the BIOS).

The newer revisions of the Dothan family that you speak off (i.e. the 740 et. al.) are of stepping C0, they do not suffer from two PAE (paging mode C) related errata: W25 and W40 as described in: [Intel Celeron M Specification Update]("http://download.intel.com/support/processors/mobile/celeron/sb/30030336.pdf")*. The Dothan 735 is of stepping B1 which is affected by them.

What I need to know is if the compiled stock kernel / compiler implemented work-arounds for the W25 and W40 errata* to the Dothan (stepping B1) family of processors. 
If that is so, then the PAE flag can be set / forced without problems.

I'd be impressed if someone could answer that.

* Brief description of the errata:
[QUOTE=Intel Celeron M Specification Update errata]
W25: Upper Four PAT Entries Not Usable with Mode B or Mode C Paging

W40: INIT Does Not Clear Global Entries in the TLB
Problem:  INIT may not flush a TLB entry when: 
1.  The processor is in protected mode with paging enabled and the page global 
enable flag is set (PGEbit of CR4 register) 
2.  G bit for the page table entry is set 
3.  TLB entry is present in TLB when INIT occurs 
Implication:  Software may encounter unexpected page fault or incorrect address 
translation due to a TLB entry erroneously left in TLB after INIT. 
Workaround: Write to CR3, CR4 (settingbits PSE, PGE or PAE) or CR0 (setting bits PG or PE)
registers before writing to memory early in BIOS code to clear all the global entries 
from TLB.
[/QUOTE]

---

### Post by sudodus on 2016-06-05
I am not a kernel programmer. I suggest that you try via other channels to find a developer or advanced tester who really knows. (Developers seldom visit the Ubuntu Forums.)

You can try via IRC or via writing a bug report at Launchpad. But I think it might be difficult to get attention for such old hardware.

IRC: [http://webchat.freenode.net/?channels=ubuntu](http://webchat.freenode.net/?channels=ubuntu)

Launchpad: [https://launchpad.net/](https://launchpad.net/)

---

### Post by mörgæs on 2016-06-06
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by martinr on 2016-06-06
Hi Mörgæs, thanks for having a look.

Here's the output from: 
sudo lshw -sanitize > lshw.txt
(Handy option -sanitize)
```

computer
    description: Notebook
    version: *
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=notebook uuid=[REMOVED]
  *-core
       description: Motherboard
       product: Mimid
       vendor: Acer
       physical id: 0
       version: *
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V2.90
          date: 05/19/2006
          size: 84KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot socketedrom edd int13floppynec int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.70GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.6
          slot: uFCPGA
          size: 600MHz
          capacity: 1700MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: burst internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 400 MHz (2,5 ns)
             physical id: 0
             slot: DRAM Slot 0
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: SODIMM DDR Synchronous 400 MHz (2,5 ns)
             physical id: 1
             slot: DRAM Slot 1
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d0000000-d007ffff ioport:e000(size=8) memory:a0000000-afffffff memory:d0080000-d00bffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d0100000-d017ffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:296 ioport:c000(size=8192) memory:c8000000-cfffffff ioport:98000000(size=134217728)
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:297 ioport:a000(size=8192) memory:c4000000-c7ffffff ioport:94000000(size=67108864)
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1200(size=32)
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1220(size=32)
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1240(size=32)
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1260(size=32)
        *-usb:4
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:80000000-800003ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:8000(size=8192) memory:bc000000-c3ffffff ioport:8c000000(size=134217728)
           *-network:0
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@0000:05:01.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=128 link=no multicast=yes port=twisted pair speed=10Mbit/s
                resources: irq:21 memory:bc002000-bc003fff
           *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@0000:05:02.0
                logical name: eth1
                version: 05
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=[REMOVED] latency=128 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:22 memory:bc000000-bc000fff
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:c0000000-c0000fff ioport:8400(size=256) ioport:8000(size=256) memory:8c000000-8fffffff memory:84000000-87ffffff
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:e100(size=256) ioport:e200(size=64) memory:d00c0000-d00c01ff memory:d00c0200-d00c02ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:e300(size=256) ioport:e400(size=128)
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1100(size=16)
           *-disk
                description: ATA Disk
                product: HTS421280H9AT00
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: HA3O
                serial: [REMOVED]
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e233bc5d
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: [REMOVED]
                   size: 3992MiB
                   capacity: 3992MiB
                   capabilities: primary boot fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: [REMOVED]
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=512 created=2012-09-10 18:49:50 filesystem=ntfs label=ACER state=clean
              *-volume:2
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: FAT32
                   serial: [REMOVED]
                   size: 4456MiB
                   capacity: 4486MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 47GiB
                   capacity: 47GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2055MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: W95 FAT32 partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 4486MiB
                 *-logicalvolume:2
                      description: W95 FAT32 partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 22GiB
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      logical name: /
                      capacity: 18GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD writer
                product: DVD-RW DVR-K16RA
                vendor: PIONEER
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 1.25
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1400(size=32)
  *-battery
       description: Lithium Ion Battery
       product: *
       vendor: Acer
       physical id: 1
       version: *
       serial: [REMOVED]
       slot: 1st Battery
       capacity: 32000mWh
       configuration: voltage=14,8V

```

---

### Post by houstonbofh on 2016-06-06
This is a known manufacture issue.  Early Pentium Ms supported PAE, but the BIOS did not advertise the flag.  If you get it installed and boot, PAE works fine.  I have 2 old laptops were the easy fix was to install Ubuntu to the hard drive on another machine and then stick it back in there.  The "forcepae" option makes it much easier.

---

### Post by martinr on 2016-06-06
Then I suppose that the situation should be fixed in the newest [Linux Processor Microcode Data File]("https://downloadcenter.intel.com/download/25512/Linux-Processor-Microcode-Data-File") from Intel (Date: 11/9/2015). The newest 735 definitions are contained in that file. I'm not sure if the new Linux Processor Microcode Data File takes care of the PAE flag though. Furthermore I'm not sure if that data file can be made effective at boot time (overruling the BIOS). I read that it is contained in Ubuntu package: "intel-microcode", but I don't know how to make that active at boot time?

Does PAE always kick in? or only when addressing beyond 4 GB? 

For the Dothan 735 there are two errata published by Intel that are related to PAE (see above). Are there work-arounds (i suppose implemented by the compiler) in place for those in the stock kernel? or in the BIOS or the microcode? Might that be the reason that the PAE flag is not set?

I did some read-up on Intel microcode and it's fascinating.
It's clouded by proprietary secret-ism. Apparently it's firmware for the processor that can fix errata and who knows what more. It can be installed via the BIOS and/or Windows update and via Linux as well. The updates are distributed as time coded encrypted blobs. Nobody except Intel knows what's in them, nobody can verify them and once installed they cannot be rolled back to a previous version. (Also have a look at this article about security concerns: [32c3 Security concerns around Intel's x86 processors]("http://www.theregister.co.uk/2015/12/31/rutkowska_talks_on_intel_x86_security_issues/") ). So Intel can apparently fix the PAE flag issue after release of the processor.

---

### Post by QLee on 2016-06-07
> **martinr said:**
> Then I suppose that the situation should be fixed in the newest [Linux Processor Microcode Data File]("https://downloadcenter.intel.com/download/25512/Linux-Processor-Microcode-Data-File") from Intel (Date: 11/9/2015). The newest 735 definitions are contained in that file. I'm not sure if the new Linux Processor Microcode Data File takes care of the PAE flag though. Furthermore I'm not sure if that data file can be made effective at boot time (overruling the BIOS). I read that it is contained in Ubuntu package: "intel-microcode", but I don't know how to make that active at boot time?


I have no idea what effect making the code "active" at boot time will have or if it will address your trouble but my default install of 16.04 has /etc/modprobe.d/intel-microcode-blacklist.conf which would appear to cause the system to ignore.

> # The microcode module attempts to apply a microcode update when
# it autoloads.  This is not always safe, so we block it by default.
blacklist microcode 

Perhaps that is keeping the microcode that you appear to want from acting.

---

### Post by mörgæs on 2016-06-08
I don't think Intel considers the missing PAE flag an error which needs correction. They have a long history of deliberately disabling cache and other properties on well-functioning CPUs if they believed that it could make their prime brands sell better. 

Anyway, forcepae raises the PAE flag, effectively fixing the bug. 

I share your concerns about firmware. If people want to plant code in a computer running an open source operative system there are not many places to hide. Firmware is one of the few places.

---

### Post by martinr on 2016-06-09
Is there a way to find out which Pentium M 735 microcode/firmware version is contained in the "intel-microcode" package under Ubuntu?

Currently the following version of microcode is active:
```
$ grep microcode /proc/cpuinfo
microcode       : 0x17

```

---

### Post by martinr on 2016-06-12
I bluntly installed the "intel-microcode" package.
Automatically after install the microcode was directly updated.

```

dmesg output:
[ 2448.936598] microcode: CPU0 sig=0x6d6, pf=0x20, revision=0x17
[ 2448.972178] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[ 2449.162951] microcode: CPU0 updated to revision 0x18, date = 2004-10-17

$ grep microcode /proc/cpuinfo
microcode       : 0x18

```
The date riddles me, because the last available and installed BIOS update was from 2008, so revision 0x18, date = 2004-10-17 should have been available for a long time by then.

(I still haven't figured out how to list the microcode versions in the /usr/share/misc/intel-microcode.dat file from the "intel-microcode" package.)
The suggestion on [https://wiki.debian.org/Microcode?action=diff&rev1=2&rev2=3](https://wiki.debian.org/Microcode?action=diff&rev1=2&rev2=3) and the referenced [https://wiki.archlinux.org/index.php/Microcode](https://wiki.archlinux.org/index.php/Microcode) don't work:
```
$ iucode_tool -tb -lS /usr/share/misc/intel-microcode.dat
iucode_tool: cpuid kernel driver unavailable, cannot scan system processor signatures
iucode_tool: microcode bundle /usr/share/misc/intel-microcode.dat: unknown microcode format
```

Furthermore the microcode definitions aren't up to date. The "intel-microcode" package contains the defenitions from /*  Tue Jun 24 21:29:53 CST 2014  */.
The update utility doesn't work either:
```

$ sudo update-intel-microcode 
failed to download microcode index - 404

```
Just download them manually from [https://downloadcenter.intel.com/download/25512/Linux-Processor-Microcode-Data-File](https://downloadcenter.intel.com/download/25512/Linux-Processor-Microcode-Data-File) and place them in: /usr/share/misc/intel-microcode.dat

Now the question remains, will the new microcode be effective at boot time? because it seems that the microcode needs to be installed [at every new boot]("https://wiki.debian.org/Microcode?action=diff&rev1=2&rev2=3").

---

