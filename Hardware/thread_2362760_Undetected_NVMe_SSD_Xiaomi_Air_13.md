---
title: "Undetected NVMe SSD Xiaomi Air 13"
date: 2017-06-01
forum: Hardware
---

### Post by attssystem on 2017-06-01
I recently ran into problems using Windows (10) with BSOD ("CRITICAL PROCESS DIED"). After a considerable effort I succeeded wipe my SSD from within using Windows but when using Ubuntu it doesn't detect my SSD. It's not a driver issue, I already installed Ubuntu a few weeks ago and then delete it, it can't the wipe because I tried Ubuntu before considering wipe from within. But even if it isn't detected, lspci returns something like "Non Volatile Memory... Samsung..." (the SSD controller in fact) and lshw sees it as a storage but "UNCLAIMED". Gparted doesn't see it (as fdisk and parted) but on Arch I detected with fdisk -l during only 10 seconds and it said there was an I/o error (bad sector 8) but then I tried fsck and the SSD wasn't detected anymore so I gave up. A bootable USB of Windows doesn't detect it either so I don't know what to do... Thanks by advance for your help!

---

### Post by QIII on 2017-06-01
Hello!

It would be very helpful if you would post back the entire output of the lshw and lspci commands.

Is this an M.2 device or SATA?

---

### Post by attssystem on 2017-06-01
M2, I'll give you the output after dinner (30min)^^

lspci :

```

00:00.0 Host bridge: Intel Corporation Skylake Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 520 (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 940MX] (rev a2)
02:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
03:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM951/PM951 (rev 01)
```

lshw :

```

ubuntu                      
    description: Notebook
    product: TM1613 (Sku Number)
    vendor: Timi
    version: A05
    serial: 13138/00096119
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
    configuration: chassis=notebook family=Timibook sku=Sku Number uuid=1E3777FB-DEB3-E611-E89E-7FB2C9C57C7A
  *-core
       description: Motherboard
       product: TM1613
       vendor: Timi
       physical id: 0
       version: A05
       serial: MMG5S000000226BMP019H
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: A05
          date: 08/11/2016
          size: 128KiB
          capacity: 8128KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 2794MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 8
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-cache
          description: L1 cache
          physical id: 5
          slot: L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous 2133 MHz (0.5 ns)
             product: M471A1K43BB0-CPB
             vendor: Samsung
             physical id: 0
             serial: 00000000
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:1
             description: [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: [empty]
             physical id: 2
             slot: ChannelB-DIMM0
        *-bank:3
             description: [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-pci
          description: Host bridge
          product: Skylake Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 08
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: HD Graphics 520
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:278 memory:a2000000-a2ffffff memory:b0000000-bfffffff ioport:5000(size=64) memory:c0000-dffff
        *-usb
             description: USB controller
             product: Sunrise Point-LP USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:122 memory:a4200000-a420ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.10.0-19-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.10
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Mass storage device
                   product: Mass Storage Device
                   vendor: Generic
                   physical id: 1
                   bus info: usb@1:1
                   logical name: scsi2
                   version: 1.00
                   serial: 00000000000006
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      vendor: Verbatim
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sda
                      version: 0.00
                      size: 29GiB (31GB)
                      capabilities: removable
                      configuration: ansiversion=2 logicalsectorsize=512 sectorsize=512
                    *-medium
                         physical id: 0
                         logical name: /dev/sda
                         size: 29GiB (31GB)
                         capabilities: partitioned partitioned:dos
                         configuration: signature=03c8bd60
                       *-volume
                            description: Windows FAT volume
                            vendor: SYSLINUX
                            physical id: 1
                            logical name: /dev/sda1
                            logical name: /cdrom
                            version: FAT32
                            serial: 6028-aabe
                            size: 29GiB
                            capacity: 29GiB
                            capabilities: primary bootable fat initialized
                            configuration: FATs=2 filesystem=fat label=UBUNTU 17_0 mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
              *-usb:1
                   description: Video
                   product: XiaoMi USB 2.0 Webcam
                   vendor: Chicony
                   physical id: 5
                   bus info: usb@1:5
                   version: 34.05
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:2
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 7
                   bus info: usb@1:7
                   version: 0.01
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.10.0-19-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.10
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-communication
             description: Communication controller
             product: Sunrise Point-LP CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:282 memory:a422a000-a422afff
        *-storage
             description: SATA controller
             product: Sunrise Point-LP SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:275 memory:a4228000-a4229fff memory:a422d000-a422d0ff ioport:5080(size=8) ioport:5088(size=4) ioport:5060(size=32) memory:a422b000-a422b7ff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:4000(size=4096) memory:a3000000-a3ffffff ioport:90000000(size=301989888)
           *-display
                description: 3D controller
                product: GM108M [GeForce 940MX]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nouveau latency=0
                resources: irq:277 memory:a3000000-a3ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:4000(size=128)
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:a4100000-a41fffff
           *-network
                description: Wireless interface
                product: Wireless 8260
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 3a
                serial: a0:c5:89:44:79:a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-19-generic firmware=22.391740.0 ip=192.168.0.25 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:283 memory:a4100000-a4101fff
        *-pci:2
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #9
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) memory:a4000000-a40fffff
           *-storage UNCLAIMED
                description: Non-Volatile memory controller
                product: NVMe SSD Controller SM951/PM951
                vendor: Samsung Electronics Co Ltd
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express cap_list
                configuration: latency=0
                resources: memory:a4000000-a4003fff ioport:3000(size=256)
        *-isa
             description: ISA bridge
             product: Sunrise Point-LP LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory
             description: Memory controller
             product: Sunrise Point-LP PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: driver=intel_pmc_core latency=0
             resources: irq:0 memory:a4224000-a4227fff
        *-multimedia
             description: Audio device
             product: Sunrise Point-LP HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:284 memory:a4220000-a4223fff memory:a4210000-a421ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Sunrise Point-LP SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 21
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:a422c000-a422c0ff ioport:5040(size=32)
```

---

### Post by oldfred on 2017-06-02
Is drive set for AHCI, not old IDE nor RAID in UEFI? 
Also not some Intel SRT or similar settings that look like RAID to Linux?

Also updating UEFI from vendor resets settings to defaults. I have to keep  a list of setting changes as I have to or desire to make several changes.

---

### Post by attssystem on 2017-06-03
My UEFI is really simple, I don't see this kind of options. And for the reset I have an option and it didn't change anything.

---

### Post by oldfred on 2017-06-03
Generally you do not want defaults in UEFI. I have to change many settings to optimize my UEFI, several are required just to make it work. But mine is a motherboard with lots of settings.

It says it is an Insyde UEFI, which is one of the standard vendors of UEFI.

 Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A) 


Even different brand has Insyde. old thread as 12.04 now obsolete.
 Sony VAIO with Insyde H2O EFI bios Ubuntu 12.04 Dual Boot 
[http://www.linuxrelease.com/2012/07/sony-vaio-with-insyde-h2o-efi-bios.html](http://www.linuxrelease.com/2012/07/sony-vaio-with-insyde-h2o-efi-bios.html)

---

### Post by attssystem on 2017-06-03
I can't find this kind of solution for my laptop but I'm still looking for it but I'm wondering, if I already installed Ubuntu (which isn't installed no more), why, this time, would I need to change anything that requires an unlocked uefi?

---

### Post by oldfred on 2017-06-03
Did any settings change or did you update UEFI which may have changed settings.
Windows also with UEFI can change some settings.

---

### Post by attssystem on 2017-06-03
I didn't update the UEFI but I may changed some settings. However, I tried every possibilities in the UEFI, (not a lot because there is only a few different settings). What Windows could have done?

---

### Post by oldfred on 2017-06-03
Only some UEFI settings can be changed, primarily boot order which is almost always changed with updates both by Windows & Ubuntu's grub.

May then be best to post screen shots.

You can compare some of your settings to these:
 Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by attssystem on 2017-06-03
[https://pokepolitique.xyz/owncloud/index.php/s/LnW261jZPgYw1Rs](https://pokepolitique.xyz/owncloud/index.php/s/LnW261jZPgYw1Rs)

Here are your screenshots

---

### Post by oldfred on 2017-06-03
That is pretty limited.
I do not see anything there that should need changing.

Are there any submenus? It shows a key for that, but may only apply in a few cases?

---

### Post by attssystem on 2017-06-03
No submenus, unfortunately. Do you mean the secure boot keys? Because I can only clear it.

---

### Post by oldfred on 2017-06-03
I am out of ideas.
That it worked once and now does not work seems very strange.
Are you sure the live installer was not corrupted somehow?

---

### Post by attssystem on 2017-06-03
I tried a lot of USB sticks, of versions (16.04, 17.04, 17.10) and even Arch which detected my SSD for 6 seconds (said "bad sector 8) but nothing had been created under /dev but I didn't succeed redetect it since.

---

### Post by oldfred on 2017-06-03
Then it sounds like an SSD issue.
Wiping SSD can overdo the erase process.

Does UEFI show drive?
Does Disks show drive and status as good?
[https://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/](https://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/)

---

### Post by attssystem on 2017-06-04
My UEFI does show the drive but how can I use Disks if fdisk -l doesn't return my disk but only the USB stick? By the way : https://pokepolitique.xyz/owncloud/index.php/s/LnW261jZPgYw1Rs look at the last photo, could this help you?

---

### Post by oldfred on 2017-06-04
I have seen a variety of boot options relating to ACPI.

You can experiment if you can get to grub menu. Add on linux line replacing quiet splash like nomodeset.
acpi=off  worked for HP2000 
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                     
acpi=0 

      At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by attssystem on 2017-06-04
So, do you think it is relevant?

---

### Post by attssystem on 2017-06-04
Only "nomodeset" had a beneficial effects (no more acpi errors) and *-storage is now CLAIMED (it isn't UNCLAIMED in fact) but I still can't detected the SSD using fdisk.

---

### Post by oldfred on 2017-06-04
Did you try nomodeset & some of the other boot parameters?

Does disks or gparted show drive?

---

### Post by attssystem on 2017-06-04
Yes I did, and neither gparted and disks see the drive.

---

### Post by oldfred on 2017-06-04
Some have posted that firmware updates are required on/in SSD. 
No idea how to do that with your SSD.

---

### Post by attssystem on 2017-06-05
I tried using Samsung Magician on Ubuntu but it didn't detect my SSD

---

### Post by oldfred on 2017-06-05
Google found these, but I cannot suggest anything else.
But they do not mention not seeing SSD.

[https://wiki.archlinux.org/index.php/Xiaomi_Mi_Notebook_Air_13.3](https://wiki.archlinux.org/index.php/Xiaomi_Mi_Notebook_Air_13.3)

[https://www.youtube.com/watch?v=6GtbU1QGVOE](https://www.youtube.com/watch?v=6GtbU1QGVOE)

[https://askubuntu.com/questions/829863/wi-fi-drivers-for-laptop-xiaomi-air-13](https://askubuntu.com/questions/829863/wi-fi-drivers-for-laptop-xiaomi-air-13)

---

### Post by attssystem on 2017-06-05
So I'll keep looking for a solution, however, thanks for your help!

---

### Post by attssystem on 2017-06-06
```
 nvme nvme 0: I/O 237 QID 0 timeout, reset controller 
```
Can't this be relevant?

---

### Post by attssystem on 2017-06-08
Up

---

### Post by oldfred on 2017-06-08
Was that part of boot?

My syslog has this, but I do not have NVMe. But it just shows loading.
pciehp: PCI Express Hot Plug Controller Driver version: 0.4
All the rest of controller are related to USB.

Google search on that error. You may want to see if any others apply.
[http://lists.infradead.org/pipermail/linux-nvme/2017-February/008371.html](http://lists.infradead.org/pipermail/linux-nvme/2017-February/008371.html)
You may need kernel 4.11 or newer.

---

### Post by attssystem on 2017-06-08
No, it appears after using fdisk -l

---

