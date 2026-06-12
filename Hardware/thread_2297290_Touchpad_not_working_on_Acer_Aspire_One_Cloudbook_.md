---
title: "Touchpad not working on Acer Aspire One Cloudbook 11"
date: 2015-10-02
forum: Hardware
---

### Post by mvelinder on 2015-10-02
I can't seem to get the touchpad to work on 14.04 LTS on my Acer Aspire One Cloudbook 11. A USB mouse works fine. I have 14.04 on a separate partition from Windows 10. I have updated all packages using sudo apt-get update and sudo apt-get upgrade. 


I've also tried the many suggestions I've found from searches, including:


sudo modprobe -r psmouse


sudo modprobe psmouse proto=imps


and 


sudo modprobe -r psmouse


sudo modprobe psmouse


in Terminal. Neither seem to do anything. The touchpad has a toggle via Fn+F7, but the toggle doesn't seem to effect anything. The Fn+F... works for muting and volume and other keys though. 


Distro: 14.04 LTS
Kernel: 3.19.0-30-generic


Any help would be very much appreciated!

---

### Post by mvelinder on 2015-10-02
Changing Touchpad to Basic in BioS appears to fix this! As per this suggestion: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1487748/comments/2](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1487748/comments/2) Cursor movement, left click, right click, and two finger scrolling seems to work! About everything I can think I'd need. Seems solved.

---

### Post by Justin_Parus on 2015-10-07
Could you give me some more details on how you got this to install?  I keep getting a kernel panic "IO-APIC + timer," tried with couple combinations of boot options to no avail, namely: noapic, nolapic, acpi=off. Seems like the boot options aren't even being passed when the installer attempts the install. 

I am using the 14.04.3 LTS ISO written directly to a USB; maybe you have a slightly different boot media set up? What is your BIOS version? 
BIOS settings: 
```
Legacy Boot:  Enabled
TPM:  Off
Trackpad Mode: Basic
```

I was trying to set up the Asus x205ta (near impossible and annoying with a 32bit uefi and 64 bit chip. wireless barely works and sleep does not work), but I heard this Acer works almost out of the box. Any help is greatly appreciated, I am in the thick of school and don't have a lot of time to try and make this work.:-(

The x205ta charger was better in terms of portability but thats about it....

---

### Post by manurss on 2015-11-30
> **Justin_Parus said:**
> Could you give me some more details on how you got this to install?  I keep getting a kernel panic "IO-APIC + timer," tried with couple combinations of boot options to no avail, namely: noapic, nolapic, acpi=off. Seems like the boot options aren't even being passed when the installer attempts the install. 

I am using the 14.04.3 LTS ISO written directly to a USB; maybe you have a slightly different boot media set up? What is your BIOS version? 
BIOS settings: 
```
Legacy Boot:  Enabled
TPM:  Off
Trackpad Mode: Basic
```

I was trying to set up the Asus x205ta (near impossible and annoying with a 32bit uefi and 64 bit chip. wireless barely works and sleep does not work), but I heard this Acer works almost out of the box. Any help is greatly appreciated, I am in the thick of school and don't have a lot of time to try and make this work.:-(

The x205ta charger was better in terms of portability but thats about it....

I have the same problem. I try with the pendrive in oder pc´s and it works. Also it works in the pc that is in the shop (is the same model!!) with exactly the same parameters in the bios.
I just just can get it working with all the flags in the grub on, but this make that the pc cant read the batery or the disk (and say is not space for the instalation).
By normal i can see the grub but when i select an option y get a black screen and nothing happens (black screen but light on). 

Please help us: bios parameters, turn off something in windows?, tool to make the pendrive, etc.
Thank you so much.

---

### Post by mvelinder on 2015-12-01
How I got Ubuntu installed? It installed without any problems just using the disk iso (64-bit) from the Ubuntu website and making a USB disk using UNetbootin. I should also say that this is a clean reformat and fresh install of 14.04, not doing a dual boot. If you're comfortable wiping Windows and doing an Ubuntu only machine that might also help the problem. My BIOS settings are:

Network Boot: Enabled
F12 Boot Menu: Enabled
Touchpad: Basic
Lid Open Resume: Enabled
D2D Recovery: Enabled

Boot Mode: Legacy

System BIOS Version: v1.05 (Rev 5.0)

If you mean how I got the trackpad to work, just follow the instructions from the link above:
> [COLOR=#333333][FONT=monospace]Workaround: at boot, press F2 to get into BIOS, then set trackpad to Basic instead of Advanced.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]This even lets you scroll with a two-fingered gesture, and changes the output of
cat /proc/bus/input/devices to:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse1 event8
B: PROP=5
B: EV=b
B: KEY=e520 610000 0 0 0 0
[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]B: ABS=660800011000003[/FONT][/COLOR]

Hope that helps!

---

### Post by manurss on 2015-12-02
Thank you :)
Didn´t work (no just with you settings, i also try with a lot of bios settings combinations). The only explication that i have is that between markets or units it can be some diferrent peaces of some hardware. An unfortunately my model as something that linux doesn´t like.

---

### Post by mvelinder on 2015-12-02
Here's the results from sudo lshw on the machine, maybe that'll help:

> aspire                        description: Notebook
    product: Aspire one 1-131 (AO1-131_106C_1.05)
    vendor: Acer
    version: V1.05
    serial: NXSHFAA003533069062300
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 vsyscall32
    configuration: boot=normal chassis=notebook family=BSW sku=AO1-131_106C_1.05 uuid=EBA8DFDA-7982-F648-9616-58EA43AB8E34
  *-core
       description: Motherboard
       product: Caltech
       vendor: Acer
       physical id: 0
       version: V1.05
       serial: NBSHF11001531026A32300
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: V1.05
          date: 07/22/2015
          size: 128KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU  N3050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Celeron(R) CPU  N3050  @ 1.60GHz
          serial: To Be Filled By O.E.M.
          slot: CHV
          size: 2249MHz
          capacity: 2249MHz
          width: 64 bits
          clock: 83MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch ida arat epb dtherm tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: K4BDG1646Q-HYKO
             vendor: Samsung
             physical id: 0
             serial: 00000000
             slot: ChannelA-DIMM0
             size: 2GiB
             width: 8 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 21
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915_bpo latency=0
             resources: irq:311 memory:90000000-90ffffff memory:80000000-8fffffff ioport:1000(size=64)
        *-generic:0
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:21 memory:9131c000-9131cfff
        *-generic:1
             description: SD Host controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci-pci latency=0
             resources: irq:16 memory:91321000-91321fff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:115 memory:91300000-9130ffff
        *-generic:2
             description: DMA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 18
             bus info: pci@0000:00:18.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm eisa_dma bus_master cap_list
             configuration: driver=dw_dmac_pci latency=0
             resources: irq:17 memory:91318000-9131bfff
        *-serial:0
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 18.1
             bus info: pci@0000:00:18.1
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=i2c-designware-pci latency=0
             resources: irq:17 memory:9131f000-9131ffff
        *-generic:3
             description: Encryption controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:310 memory:91200000-912fffff memory:91100000-911fffff
        *-multimedia
             description: Audio device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:312 memory:91310000-91313fff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:2000(size=4096) memory:91400000-915fffff ioport:91600000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 memory:91000000-910fffff
           *-network
                description: Wireless interface
                product: Wireless 3160
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 83
                serial: b4:6d:83:48:a3:87
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-37-generic firmware=25.17.12.0 ip=192.168.1.239 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:313 memory:91000000-91001fff
        *-generic:4
             description: DMA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm eisa_dma bus_master cap_list
             configuration: driver=dw_dmac_pci latency=0
             resources: irq:19 memory:91314000-91317fff
        *-communication
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1e.4
             bus info: pci@0000:00:1e.4
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:19 memory:9131e000-9131efff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-serial:1 UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:9131d000-9131d01f ioport:1040(size=32)

---

### Post by eival on 2016-06-08
> **mvelinder said:**
> Changing Touchpad to Basic in BioS appears to fix this! As per this suggestion: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1487748/comments/2](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/1487748/comments/2) Cursor movement, left click, right click, and two finger scrolling seems to work! About everything I can think I'd need. Seems solved.

HA, thank you, this fixed it for Windows 10 as well, ever since i got this laptop and put a clean install of Win10 i couldnt figure out how to do this

---

