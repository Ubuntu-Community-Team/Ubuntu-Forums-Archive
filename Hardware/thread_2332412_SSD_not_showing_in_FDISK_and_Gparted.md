---
title: "SSD not showing in FDISK and Gparted"
date: 2016-07-31
forum: Hardware
---

### Post by genz10 on 2016-07-31
Hi all, I was tried to install ubuntu 16.04 in my laptop that previously using windows 8. But when I try to install it, the installer can't detect my SSD, and displayed error message that my space doens't enough for installing ubuntu. When I try to google it , I found that the ubuntu didn't recognize my SSD , but it was detected in BIOS and I already set in AHCI mode. Gparted also can't detect my SSD and my harddrive still running well in windows. I have tried to google it using any keyword that cross my mind but can't find the exact solution for my problem.  Does anyone know the solution? here's my fdisk -l result:

```
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1459982336 bytes, 2851528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 7.5 GiB, 8002732032 bytes, 15630336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *     2048 15630335 15628288  7.5G  c W95 FAT32 (LBA)


```

Thank you so much

---

### Post by oldfred on 2016-07-31
Post these:
       sudo parted /dev/sda unit s print
sudo gdisk -l /dev/sda

---

### Post by genz10 on 2016-07-31
Hi, thanks for your reply :)

```
ubuntu@ubuntu:~$ sudo parted /dev/sda/ unit s print
Error: Could not stat device /dev/sda/ - No such file or directory.
Retry/Cancel? ^C                                                          
ubuntu@ubuntu:~$ sudo gdisk -l dev/sda
sudo: unable to execute /sbin/gdisk: Input/output error


```

---

### Post by oldfred on 2016-07-31
Nothing seems to see drive.
Is this a standard drive or a new NVMe drive?

What brand/model system?

In Disks and icon in upper right corner is Smart Data. Does it see drive?

---

### Post by genz10 on 2016-08-01
in Disks also doesn't show anything.

I use SSD Transcend 256GB 6GB/S

But the harddisk is detected and running normally in windows.

---

### Post by oldfred on 2016-08-01
This user has a 128GB Transend and it just worked.
[URL="http://karuppuswamy.com/wordpress/2014/06/26/everything-you-need-to-know-about-ssd-support-in-ubuntu-14-04/"]http://karuppuswamy.com/wordpress/2014/06/26/everything-you-need-to-know-about-ssd-support-in-ubuntu-14-04/
[http://www.phoronix.com/scan.php?page=article&item=transcend-ssd370-256gb&num=1](http://www.phoronix.com/scan.php?page=article&item=transcend-ssd370-256gb&num=1)
[/URL]

---

### Post by genz10 on 2016-08-01
> **oldfred said:**
> This user has a 128GB Transend and it just worked.
[URL="http://karuppuswamy.com/wordpress/2014/06/26/everything-you-need-to-know-about-ssd-support-in-ubuntu-14-04/"]http://karuppuswamy.com/wordpress/2014/06/26/everything-you-need-to-know-about-ssd-support-in-ubuntu-14-04/
[/URL][http://www.phoronix.com/scan.php?page=article&item=transcend-ssd370-256gb&num=1](http://www.phoronix.com/scan.php?page=article&item=transcend-ssd370-256gb&num=1)


I have read both source, it even doens't show any drive on /dev/sda . I had tried run any command on ubuntu but none of them is showing existence of my SSD.

---

### Post by oldfred on 2016-08-01
Is there any sort of setting in UEFI for locking the drive.
A few users have said they had issues with that, but I think drive was still seen, just not usable.

---

### Post by genz10 on 2016-08-01
> **oldfred said:**
> Is there any sort of setting in UEFI for locking the drive.
A few users have said they had issues with that, but I think drive was still seen, just not usable.

Unfortunately my laptop seems dont have any UEFI settings. here's my BIOS photos. 

My drive not detected in Gparted, Disks and fdisk -l

[http://prntscr.com/c09jgy](http://prntscr.com/c09jgy)
[http://prntscr.com/c09jgj](http://prntscr.com/c09jgj)
[http://prntscr.com/c06wlm](http://prntscr.com/c06wlm)

---

### Post by weatherman2 on 2016-08-01
Under the "Advanced" menu in BIOS, try changing your SATA Configuration and see if anything changes in Ubuntu.  (You may not be able to boot Windows anymore if you change it to something else, at least until you change it back to what it is now.)

You could sift through the output of the "dmesg" command.  Or post the output here of "sudo lshw"

---

### Post by oldfred on 2016-08-01
I have seen where some of the Intel settings can interfere.
And Intel anti-theft may be an issue what shows under that?

Did you say what brand/model system?

And some users have had to turn on legacy/BIOS/CSM settings but still boot in UEFI mode?
Most usually have to make sure CSM is off, to be able to correctly boot in UEFI mode.

---

### Post by genz10 on 2016-08-01
> **weatherman2 said:**
> Under the "Advanced" menu in BIOS, try changing your SATA Configuration and see if anything changes in Ubuntu.  (You may not be able to boot Windows anymore if you change it to something else, at least until you change it back to what it is now.)

You could sift through the output of the "dmesg" command.  Or post the output here of "sudo lshw"

Under SATA Configuration there's only AHCI mode and no other option. Here is the result of "sudo lshw"
```
  description: Notebook
    product: TP550LD (ASUS-NotebookSKU)
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: EAN0WU32717143A
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=TP sku=ASUS-NotebookSKU uuid=608A8162-F579-47F5-866B-AC9E178FB0EB
  *-core
       description: Motherboard
       product: TP550LD
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: TP550LD.210
          date: 06/27/2014
          size: 64KiB
          capacity: 6080KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-4030U CPU @ 1.90GHz
          vendor: Intel Corp.
          physical id: 8
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-4030U CPU @ 1.90GHz
          slot: SOCKET 0
          size: 1800MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer xsave avx f16c rdrand lahf_lm abm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm arat pln pts cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L2 cache
             physical id: 9
             slot: CPU Internal L2
             size: 512KiB
             capacity: 512KiB
             capabilities: internal write-back unified
             configuration: level=2
        *-cache:1
             description: L1 cache
             physical id: a
             slot: CPU Internal L1
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back
             configuration: level=1
        *-cache:2
             description: L3 cache
             physical id: b
             slot: CPU Internal L3
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: HMT451S6AFR8A-PB
             vendor: Hynix/Hyundai
             physical id: 0
             serial: 00000000
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: ChannelA-DIMM1
        *-bank:2
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 2
             serial: [Empty]
             slot: ChannelB-DIMM0
        *-bank:3
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             serial: [Empty]
             slot: ChannelB-DIMM1
     *-pci
          description: Host bridge
          product: Haswell-ULT DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0b
          width: 32 bits
          clock: 33MHz
          configuration: driver=hsw_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Haswell-ULT Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0b
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:48 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
        *-multimedia:0
             description: Audio device
             product: Haswell-ULT HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0b
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:51 memory:f7a1c000-f7a1ffff
        *-generic:0
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 0b
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:16 memory:f7a10000-f7a17fff
        *-usb:0
             description: USB controller
             product: 8 Series USB xHCI HC
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:44 memory:f7a00000-f7a0ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-31-generic xhci-hcd
                physical id: 0
                bus info: usb@3
                logical name: usb3
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-31-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=9 speed=480Mbit/s
              *-usb:0
                   description: Bluetooth wireless interface
                   product: Bluetooth USB Host Controller
                   vendor: Atheros Communications
                   physical id: 4
                   bus info: usb@2:4
                   version: 0.02
                   serial: Alaska Day 2006
                   capabilities: bluetooth usb-1.10
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:1
                   description: Video
                   product: USB2.0 VGA UVC WebCam
                   vendor: Chicony Electronics Co., Ltd
                   physical id: 5
                   bus info: usb@2:5
                   version: 99.15
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=200mA speed=480Mbit/s
              *-usb:2
                   description: Human interface device
                   product: SiS HID Touch Controller
                   vendor: USBest Technology
                   physical id: 7
                   bus info: usb@2:7
                   version: 1.01
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
              *-usb:3
                   description: Generic USB device
                   product: USB2.0-CRW
                   vendor: Generic
                   physical id: 8
                   bus info: usb@2:8
                   version: 39.60
                   serial: 20100201396000000
                   capabilities: usb-2.00
                   configuration: driver=rtsx_usb maxpower=500mA speed=480Mbit/s
        *-communication
             description: Communication controller
             product: 8 Series HECI #0
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:49 memory:f7a25000-f7a2501f
        *-multimedia:1
             description: Audio device
             product: 8 Series HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:50 memory:f7a18000-f7a1bfff
        *-pci:0
             description: PCI bridge
             product: 8 Series PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40
        *-pci:1
             description: PCI bridge
             product: 8 Series PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:e000(size=4096) memory:f7900000-f79fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 10
                serial: ac:9e:17:8f:b0:eb
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:46 ioport:e000(size=256) memory:f7904000-f7904fff memory:f7900000-f7903fff
        *-pci:2
             description: PCI bridge
             product: 8 Series PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 memory:f7800000-f78fffff
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 01
                serial: 40:e2:30:4a:ac:bb
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=4.4.0-31-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:19 memory:f7800000-f787ffff memory:f7880000-f788ffff
        *-pci:3
             description: PCI bridge
             product: 8 Series PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:d000(size=4096) memory:f6000000-f70fffff ioport:e0000000(size=301989888)
           *-display
                description: 3D controller
                product: GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:47 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:d000(size=128) memory:f7000000-f707ffff
        *-usb:1
             description: USB controller
             product: 8 Series USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7a23000-f7a233ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.4.0-31-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.04
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
                 *-usb
                      description: Mass storage device
                      product: Cruzer Blade
                      vendor: SanDisk
                      physical id: 2
                      bus info: usb@1:1.2
                      logical name: scsi4
                      version: 1.00
                      serial: 4C530499920616122261
                      capabilities: usb-2.10 scsi emulated scsi-host
                      configuration: driver=usb-storage maxpower=224mA speed=480Mbit/s
                    *-disk
                         description: SCSI Disk
                         product: Cruzer Blade
                         vendor: SanDisk
                         physical id: 0.0.0
                         bus info: scsi@4:0.0.0
                         logical name: /dev/sda
                         version: 1.00
                         serial: 4C530499920616122261
                         size: 7632MiB (8002MB)
                         capabilities: removable
                         configuration: ansiversion=6 logicalsectorsize=512 sectorsize=512
                       *-medium
                            physical id: 0
                            logical name: /dev/sda
                            size: 7632MiB (8002MB)
                            capabilities: partitioned partitioned:dos
                          *-volume
                               description: Windows FAT volume
                               vendor: MSDOS5.0
                               physical id: 1
                               logical name: /dev/sda1
                               logical name: /cdrom
                               version: FAT32
                               serial: 488b-4f72
                               size: 7628MiB
                               capacity: 7631MiB
                               capabilities: primary bootable fat initialized
                               configuration: FATs=2 filesystem=fat label=UBUNTU 16_0 mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
        *-isa
             description: ISA bridge
             product: 8 Series LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 8 Series SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7a22000-f7a227ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7a21000-f7a210ff ioport:f040(size=32)
        *-generic:1 UNCLAIMED
             description: Signal processing controller
             product: 8 Series Thermal
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:f7a20000-f7a20fff
     *-scsi
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GUA0N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: AS00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc


```
> **oldfred said:**
> I have seen where some of the Intel settings can interfere.
And Intel anti-theft may be an issue what shows under that?

Did you say what brand/model system?

And some users have had to turn on legacy/BIOS/CSM settings but still boot in UEFI mode?
Most usually have to make sure CSM is off, to be able to correctly boot in UEFI mode.

I already tried switch to CSM and Legacy mode but I can't find the configuration to change it, and I also had tried to disabled anti theft config and still get no result.

---

### Post by weatherman2 on 2016-08-01
I'd still try sifting through the output of the command "dmesg" .  (Or /var/log/syslog .)   Can't tell you what to look for specifically.  You could try booting a live USB then pasting all of it here.

You might also try booting Ubuntu 14.04 and see if you have the same problem.  If not, could be a bug in 16.04.

---

### Post by weatherman2 on 2016-08-01
Also, I checked the support page from Asus.  There is a slightly newer BIOS (version 211) available from Asus, though their note says nothing about fixing a problem like you describe.  But sometimes problems are fixed in a BIOS that aren't noted in the release notes.

---

### Post by genz10 on 2016-08-01
> **weatherman2 said:**
> I'd still try sifting through the output of the command "dmesg" .  (Or /var/log/syslog .)   Can't tell you what to look for specifically.  You could try booting a live USB then pasting all of it here.

You might also try booting Ubuntu 14.04 and see if you have the same problem.  If not, could be a bug in 16.04.

here is the log 

```
[    1.218532] TCP: Hash tables configured (established 8192 bind 8192)
[    1.218545] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    1.218550] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    1.218590] NET: Registered protocol family 1
[    1.218604] pci 0000:00:02.0: Video device with shadowed ROM
[    1.239439] PCI: CLS 64 bytes, default 64
[    1.239495] Trying to unpack rootfs image as initramfs...
[    6.482308] Freeing initrd memory: 21052K (f676f000 - f7bfe000)
[    6.482348] DMAR: Host address width 39
[    6.482351] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    6.482367] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap c0000020660462 ecap f0101a
[    6.482369] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    6.482376] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008020660462 ecap f010da
[    6.482377] DMAR: RMRR base: 0x000000c9a95000 end: 0x000000c9aa1fff
[    6.482379] DMAR: RMRR base: 0x000000cbc00000 end: 0x000000cfdfffff
[    6.482381] DMAR: ANDD device: 1 name: \_SB.PCI0.I2C0
[    6.482389] DMAR: ACPI device "INT33C2:00" under DMAR at fed91000 as 00:15.1
[    6.482508] RAPL PMU detected, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    6.482510] hw unit of domain pp0-core 2^-14 Joules
[    6.482511] hw unit of domain package 2^-14 Joules
[    6.482512] hw unit of domain dram 2^-14 Joules
[    6.482513] hw unit of domain pp1-gpu 2^-14 Joules
[    6.482622] microcode: CPU0 sig=0x40651, pf=0x40, revision=0x17
[    6.482630] microcode: CPU1 sig=0x40651, pf=0x40, revision=0x17
[    6.482638] microcode: CPU2 sig=0x40651, pf=0x40, revision=0x17
[    6.482647] microcode: CPU3 sig=0x40651, pf=0x40, revision=0x17
[    6.482695] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    6.482789] Scanning for low memory corruption every 60 seconds
[    6.483157] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    6.483175] Initialise system trusted keyring
[    6.483199] audit: initializing netlink subsys (disabled)
[    6.483213] audit: type=2000 audit(1470109305.528:1): initialized
[    6.483579] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    6.485453] zpool: loaded
[    6.485457] zbud: loaded
[    6.485536] VFS: Disk quotas dquot_6.6.0
[    6.485577] VFS: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    6.486079] fuse init (API version 7.23)
[    6.486245] Key type big_key registered
[    6.486535] Key type asymmetric registered
[    6.486540] Asymmetric key parser 'x509' registered
[    6.486563] bounce: pool size: 64 pages
[    6.486610] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    6.486646] io scheduler noop registered
[    6.486651] io scheduler deadline registered (default)
[    6.486691] io scheduler cfq registered
[    6.487399] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    6.487404] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    6.487424] pcieport 0000:00:1c.2: Signaling PME through PCIe PME interrupt
[    6.487426] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    6.487430] pcie_pme 0000:00:1c.2:pcie01: service driver pcie_pme loaded
[    6.487450] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    6.487452] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    6.487455] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    6.487475] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    6.487477] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[    6.487480] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    6.487488] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    6.487495] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    6.487538] intel_idle: MWAIT substates: 0x11142120
[    6.487539] intel_idle: v0.4 model 0x45
[    6.487541] intel_idle: lapic_timer_reliable_states 0xffffffff
[    6.487904] ACPI: AC Adapter [AC0] (on-line)
[    6.487993] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    6.488715] ACPI: Lid Switch [LID]
[    6.488763] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    6.488767] ACPI: Sleep Button [SLPB]
[    6.488810] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    6.488813] ACPI: Power Button [PWRF]
[    6.491276] thermal LNXTHERM:00: registered as thermal_zone0
[    6.491279] ACPI: Thermal Zone [THRM] (44 C)
[    6.491350] GHES: HEST is not enabled!
[    6.491410] isapnp: Scanning for PnP cards...
[    6.491591] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    6.493696] Linux agpgart interface v0.103
[    6.496303] brd: module loaded
[    6.497374] loop: module loaded
[    6.497633] libphy: Fixed MDIO Bus: probed
[    6.497638] tun: Universal TUN/TAP device driver, 1.6
[    6.497640] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    6.497690] PPP generic driver version 2.4.2
[    6.497862] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    6.497868] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    6.498932] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x0004b810
[    6.498937] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    6.499018] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    6.499020] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    6.499022] usb usb1: Product: xHCI Host Controller
[    6.499024] usb usb1: Manufacturer: Linux 4.2.0-27-generic xhci-hcd
[    6.499026] usb usb1: SerialNumber: 0000:00:14.0
[    6.499158] hub 1-0:1.0: USB hub found
[    6.499169] hub 1-0:1.0: 9 ports detected
[    6.502299] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    6.502303] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    6.502339] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    6.502342] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    6.502344] usb usb2: Product: xHCI Host Controller
[    6.502346] usb usb2: Manufacturer: Linux 4.2.0-27-generic xhci-hcd
[    6.502349] usb usb2: SerialNumber: 0000:00:14.0
[    6.502481] hub 2-0:1.0: USB hub found
[    6.502493] hub 2-0:1.0: 4 ports detected
[    6.503508] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    6.503515] ehci-pci: EHCI PCI platform driver
[    6.503613] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    6.503619] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    6.503629] ehci-pci 0000:00:1d.0: debug port 2
[    6.507919] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    6.507929] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7a23000
[    6.512343] ACPI: Battery Slot [BAT0] (battery present)
[    6.517447] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    6.517488] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    6.517491] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    6.517493] usb usb3: Product: EHCI Host Controller
[    6.517495] usb usb3: Manufacturer: Linux 4.2.0-27-generic ehci_hcd
[    6.517496] usb usb3: SerialNumber: 0000:00:1d.0
[    6.517635] hub 3-0:1.0: USB hub found
[    6.517641] hub 3-0:1.0: 2 ports detected
[    6.517780] ehci-platform: EHCI generic platform driver
[    6.517793] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    6.517800] ohci-pci: OHCI PCI platform driver
[    6.517814] ohci-platform: OHCI generic platform driver
[    6.517825] uhci_hcd: USB Universal Host Controller Interface driver
[    6.517904] i8042: PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    6.521302] i8042: Detected active multiplexing controller, rev 1.1
[    6.523000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.523005] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    6.523042] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    6.523074] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    6.523105] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    6.523256] mousedev: PS/2 mouse device common for all mice
[    6.523448] rtc_cmos 00:02: RTC can wake from S4
[    6.523579] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    6.523605] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    6.523620] i2c /dev entries driver
[    6.523683] device-mapper: uevent: version 1.0.3
[    6.523759] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    6.523783] platform eisa.0: Probing EISA bus 0
[    6.523785] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    6.523787] platform eisa.0: Cannot allocate resource for EISA slot 1
[    6.523789] platform eisa.0: Cannot allocate resource for EISA slot 2
[    6.523790] platform eisa.0: Cannot allocate resource for EISA slot 3
[    6.523792] platform eisa.0: Cannot allocate resource for EISA slot 4
[    6.523794] platform eisa.0: Cannot allocate resource for EISA slot 5
[    6.523795] platform eisa.0: Cannot allocate resource for EISA slot 6
[    6.523797] platform eisa.0: Cannot allocate resource for EISA slot 7
[    6.523799] platform eisa.0: Cannot allocate resource for EISA slot 8
[    6.523801] platform eisa.0: EISA: Detected 0 cards
[    6.523814] cpufreq-nforce2: No nForce2 chipset.
[    6.523819] Intel P-state driver initializing.
[    6.523950] ledtrig-cpu: registered to indicate activity on CPUs
[    6.523976] PCCT header not found.
[    6.524542] NET: Registered protocol family 10
[    6.525059] NET: Registered protocol family 17
[    6.525084] Key type dns_resolver registered
[    6.525663] Using IPI No-Shortcut mode
[    6.526006] Loading compiled-in X.509 certificates
[    6.531537] Loaded X.509 cert 'Build time autogenerated kernel key: 5fb55b9a9c559d10ee627437bfa5e8c5f05ca350'
[    6.531552] registered taskstats version 1
[    6.531577] zswap: loading zswap
[    6.531579] zswap: using zbud pool
[    6.531583] zswap: using lzo compressor
[    6.533477] Key type trusted registered
[    6.536803] Key type encrypted registered
[    6.536811] AppArmor: AppArmor sha1 policy hashing enabled
[    6.536815] ima: No TPM chip found, activating TPM-bypass!
[    6.536837] evm: HMAC attrs: 0x1
[    6.537326]   Magic number: 12:608:663
[    6.537431] rtc_cmos 00:02: setting system clock to 2016-08-02 03:41:47 UTC (1470109307)
[    6.537488] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    6.537489] EDD information not available.
[    6.537603] PM: Hibernation image not present or could not be loaded.
[    6.562686] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    6.817337] usb 1-1: new high-speed USB device number 2 using xhci_hcd
[    6.848698] isapnp: No Plug & Play device found
[    6.848950] Freeing unused kernel memory: 976K (c1ac8000 - c1bbc000)
[    6.849018] Write protecting the kernel text: 7248k
[    6.849046] Write protecting the kernel read-only data: 3040k
[    6.849047] NX-protecting the kernel data: 5040k
[    6.857306] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    6.862783] systemd-udevd[110]: starting version 204
[    6.884969] sdhci: Secure Digital Host Controller Interface driver
[    6.884973] sdhci: Copyright(c) Pierre Ossman
[    6.888585] wmi: Mapper loaded
[    6.930043] [drm] Initialized drm 1.1.0 20060810
[    6.933776] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    6.933787] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    6.935460] ahci 0000:00:1f.2: version 3.0
[    6.935594] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    6.942301] r8169 0000:02:00.0 eth0: RTL8168g/8111g at 0xf8434000, ac:9e:17:8f:b0:eb, XID 10900800 IRQ 46
[    6.942306] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    6.949294] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x3 impl SATA mode
[    6.949300] ahci 0000:00:1f.2: flags: 64bit ncq stag led clo only pio slum part deso sadm sds apst 
[    6.950184] scsi host0: ahci
[    6.950331] scsi host1: ahci
[    6.950460] scsi host2: ahci
[    6.950589] scsi host3: ahci
[    6.950678] ata1: SATA max UDMA/133 abar m2048@0xf7a22000 port 0xf7a22100 irq 45
[    6.950682] ata2: SATA max UDMA/133 abar m2048@0xf7a22000 port 0xf7a22180 irq 45
[    6.950685] ata3: DUMMY
[    6.950687] ata4: DUMMY
[    7.009902] usb 1-1: New USB device found, idVendor=0781, idProduct=5567
[    7.009908] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    7.009912] usb 1-1: Product: Cruzer Blade
[    7.009915] usb 1-1: Manufacturer: SanDisk
[    7.009918] usb 1-1: SerialNumber: 4C530499920616122261
[    7.010721] pmd_set_huge: Cannot satisfy [mem 0xf7400000-0xf7600000] with a huge-page mapping due to MTRR override.
[    7.010817] [drm] Memory usable by graphics device = 2048M
[    7.010820] [drm] Replacing VGA console driver
[    7.011500] Console: switching to colour dummy device 80x25
[    7.018472] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    7.018475] [drm] Driver supports precise vblank timestamp query.
[    7.018556] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    7.024494] MXM: GUID detected in BIOS
[    7.024578] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[    7.024633] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[    7.024830] pci 0000:04:00.0: optimus capabilities: enabled, status dynamic power, 
[    7.024832] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.RP05.PEGP handle
[    7.033733] usb 3-1: New USB device found, idVendor=8087, idProduct=8000
[    7.033737] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    7.034143] hub 3-1:1.0: USB hub found
[    7.034300] hub 3-1:1.0: 8 ports detected
[    7.053666] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    7.055149] fbcon: inteldrmfb (fb0) is primary device
[    7.055779] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[    7.059304] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/LNXVIDEO:00/input/input12
[    7.060871] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    7.064273] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input13
[    7.064385] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
[    7.064800] nouveau  [  DEVICE][0000:04:00.0] BOOT0  : 0x0d7000a2
[    7.064801] nouveau  [  DEVICE][0000:04:00.0] Chipset: GF117 (NVD7)
[    7.064802] nouveau  [  DEVICE][0000:04:00.0] Family : NVC0
[    7.083975] nouveau  [   VBIOS][0000:04:00.0] using image from ACPI
[    7.084065] nouveau  [   VBIOS][0000:04:00.0] BIT signature found
[    7.084068] nouveau  [   VBIOS][0000:04:00.0] version 75.17.82.00.0a
[    7.084472] nouveau  [   VBIOS][0000:04:00.0] running init tables
[    7.166917] nouveau  [     PMC][0000:04:00.0] MSI interrupts enabled
[    7.166973] nouveau W[     PFB][0000:04:00.0][0x00000000] reclocking of this ram type unsupported
[    7.166975] nouveau  [     PFB][0000:04:00.0] RAM type: DDR3
[    7.166976] nouveau  [     PFB][0000:04:00.0] RAM size: 2048 MiB
[    7.166977] nouveau  [     PFB][0000:04:00.0]    ZCOMP: 0 tags
[    7.221209] usb 1-4: new full-speed USB device number 3 using xhci_hcd
[    7.269246] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    7.270504] ata1.00: ACPI cmd ef/10:09:00:00:00:b0 (SET FEATURES) succeeded
[    7.280073] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[    7.280074] ata1.00: failed to IDENTIFY after ACPI commands
[    7.350798] usb 1-4: New USB device found, idVendor=13d3, idProduct=3402
[    7.350799] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    7.350801] usb 1-4: Product: Bluetooth USB Host Controller
[    7.350802] usb 1-4: Manufacturer: Atheros Communications
[    7.350803] usb 1-4: SerialNumber: Alaska Day 2006
[    7.481119] tsc: Refined TSC clocksource calibration: 1895.610 MHz
[    7.481121] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x36a5f12a74d, max_idle_ns: 881590412319 ns
[    7.517084] usb 1-5: new high-speed USB device number 4 using xhci_hcd
[    7.589038] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x381f17)
[    7.604697] psmouse serio4: elantech: Synaptics capabilities query result 0x10, 0x14, 0x0e.
[    7.619302] psmouse serio4: elantech: Elan sample query result 0f, 19, 75
[    7.722708] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input11
[    7.744156] usb 1-5: New USB device found, idVendor=04f2, idProduct=b483
[    7.744157] usb 1-5: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    7.744158] usb 1-5: Product: USB2.0 VGA UVC WebCam
[    8.108855] Console: switching to colour frame buffer device 170x48
[    8.115972] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    8.115974] i915 0000:00:02.0: registered panic notifier
[    8.420773] usb 1-7: new full-speed USB device number 5 using xhci_hcd
[    8.444739] nouveau  [  PTHERM][0000:04:00.0] FAN control: none / external
[    8.444759] nouveau  [  PTHERM][0000:04:00.0] internal sensor: no
[    8.444823] nouveau  [     CLK][0000:04:00.0] 07: core 162 MHz memory 405 MHz 
[    8.444839] nouveau  [     CLK][0000:04:00.0] 0f: core 625 MHz memory 900 MHz 
[    8.445025] nouveau  [     CLK][0000:04:00.0] --: core 270 MHz memory 324 MHz 
[    8.451465] vga_switcheroo: enabled
[    8.451632] [TTM] Zone  kernel: Available graphics memory: 426834 kiB
[    8.451635] [TTM] Zone highmem: Available graphics memory: 2007682 kiB
[    8.451636] [TTM] Initializing pool allocator
[    8.451642] [TTM] Initializing DMA pool allocator
[    8.451654] nouveau  [     DRM] VRAM: 2048 MiB
[    8.451656] nouveau  [     DRM] GART: 1048576 MiB
[    8.451659] nouveau W[     DRM] Pointer to TMDS table invalid
[    8.451661] nouveau  [     DRM] DCB version 4.0
[    8.451663] nouveau W[     DRM] Pointer to flat panel table invalid
[    8.461863] nouveau  [     DRM] MM: using COPY0 for buffer copies
[    8.461870] [drm] Initialized nouveau 1.2.2 20120801 for 0000:04:00.0 on minor 1
[    8.480905] clocksource: Switched to clocksource tsc
[    8.609092] usb 1-7: not running at top speed; connect to a high speed hub
[    8.622334] usb 1-7: New USB device found, idVendor=0457, idProduct=108a
[    8.622339] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    8.622342] usb 1-7: Product: SiS HID Touch Controller
[    8.622344] usb 1-7: Manufacturer: USBest Technology
[    8.788645] usb 1-8: new high-speed USB device number 6 using xhci_hcd
[    8.916956] usb 1-8: New USB device found, idVendor=0bda, idProduct=0129
[    8.916959] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    8.916961] usb 1-8: Product: USB2.0-CRW
[    8.916963] usb 1-8: Manufacturer: Generic
[    8.916965] usb 1-8: SerialNumber: 20100201396000000
[    8.925659] usb-storage 1-1:1.0: USB Mass Storage device detected
[    8.925748] scsi host4: usb-storage 1-1:1.0
[    8.925913] usbcore: registered new interface driver usb-storage
[    8.927426] usbcore: registered new interface driver rtsx_usb
[    8.929050] hidraw: raw HID events driver (C) Jiri Kosina
[    8.932162] usbcore: registered new interface driver uas
[    8.937446] usbcore: registered new interface driver usbhid
[    8.937448] usbhid: USB HID core driver
[    9.924795] scsi 4:0:0:0: Direct-Access     SanDisk  Cruzer Blade     1.00 PQ: 0 ANSI: 6
[    9.925138] sd 4:0:0:0: Attached scsi generic sg0 type 0
[    9.925411] sd 4:0:0:0: [sda] 15630336 512-byte logical blocks: (8.00 GB/7.45 GiB)
[    9.926155] sd 4:0:0:0: [sda] Write Protect is off
[    9.926160] sd 4:0:0:0: [sda] Mode Sense: 43 00 00 00
[    9.926462] sd 4:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    9.928707]  sda: sda1
[    9.930268] sd 4:0:0:0: [sda] Attached SCSI removable disk
[   12.587303] ata1: SATA link down (SStatus 0 SControl 300)
[   12.907183] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   12.909432] ata2.00: ATAPI: HL-DT-ST DVDRAM GUA0N, AS00, max UDMA/133
[   12.911188] ata2.00: configured for UDMA/133
[   12.919253] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GUA0N     AS00 PQ: 0 ANSI: 5
[   12.945590] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   12.945594] cdrom: Uniform CD-ROM driver Revision: 3.20
[   12.945794] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   12.945903] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   13.472648] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   13.742826] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   13.743120] ACPI: \_SB_.PCI0.RP05.PEGP: failed to evaluate _DSM
[   13.743125] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   13.903702] random: nonblocking pool is initialized
[   20.144798] systemd-udevd[1024]: starting version 204
[   20.319827] lp: driver loaded but no devices found
[   20.391718] ppdev: user-space parallel port driver
[   20.645943] Bluetooth: Core ver 2.20
[   20.645965] NET: Registered protocol family 31
[   20.645967] Bluetooth: HCI device and connection manager initialized
[   20.645972] Bluetooth: HCI socket layer initialized
[   20.645976] Bluetooth: L2CAP socket layer initialized
[   20.645984] Bluetooth: SCO socket layer initialized
[   20.701819] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.701824] Bluetooth: BNEP filters: protocol multicast
[   20.701830] Bluetooth: BNEP socket layer initialized
[   20.708976] init: cups main process (1112) killed by HUP signal
[   20.708993] init: cups main process ended, respawning
[   20.739106] Bluetooth: RFCOMM TTY layer initialized
[   20.739116] Bluetooth: RFCOMM socket layer initialized
[   20.739122] Bluetooth: RFCOMM ver 1.11
[   20.764516] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.842233] genirq: Flags mismatch irq 0. 00000001 (kxcjk1013_event) vs. 00015a00 (timer)
[   20.868326] kxcjk1013: probe of i2c-SMO8500:00 failed with error -16
[   20.965670] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   20.994472] usbcore: registered new interface driver btusb
[   21.024099] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input14
[   21.024292] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input15
[   21.024456] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input16
[   21.037172] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC3236: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   21.037176] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   21.037178] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   21.037180] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[   21.037181] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[   21.037184] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x1b
[   21.082046] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input17
[   21.095051] media: Linux media interface: v0.10
[   21.125812] input: USBest Technology SiS HID Touch Controller as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/0003:0457:108A.0001/input/input18
[   21.152280] hid-multitouch 0003:0457:108A.0001: input,hiddev0,hidraw0: USB HID v1.11 Device [USBest Technology SiS HID Touch Controller] on usb-0000:00:14.0-7/input0
[   21.154687] Linux video capture interface: v2.00
[   21.221623] usb 1-4: USB disconnect, device number 3
[   21.221677] usbcore: registered new interface driver ath3k
[   21.295698] ath: phy0: Set parameters for CUS198
[   21.295703] ath: phy0: Set BT/WLAN RX diversity capability
[   21.324235] uvcvideo: Found UVC 1.00 device USB2.0 VGA UVC WebCam (04f2:b483)
[   21.327139] ath: phy0: Enable LNA combining
[   21.328278] ath: phy0: ASPM enabled: 0x42
[   21.328281] ath: EEPROM regdomain: 0x60
[   21.328283] ath: EEPROM indicates we should expect a direct regpair map
[   21.328285] ath: Country alpha2 being used: 00
[   21.328286] ath: Regpair used: 0x60
[   21.332199] device-mapper: multipath: version 1.9.0 loaded
[   21.368580] input: USB2.0 VGA UVC WebCam as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/input/input20
[   21.368685] usbcore: registered new interface driver uvcvideo
[   21.368688] USB Video Class driver (1.1.1)
[   21.371551] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   21.372303] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xf9b00000, irq=19
[   21.492149] usb 1-4: new full-speed USB device number 7 using xhci_hcd
[   21.563918] asus_wmi: ASUS WMI generic driver loaded
[   21.585675] asus_wmi: Initialization: 0x1
[   21.585729] asus_wmi: BIOS WMI version: 7.9
[   21.585790] asus_wmi: SFUN value: 0x4a0877
[   21.587370] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input21
[   21.590119] intel_rapl: Found RAPL domain package
[   21.590124] intel_rapl: Found RAPL domain core
[   21.590127] intel_rapl: Found RAPL domain uncore
[   21.590130] intel_rapl: Found RAPL domain dram
[   21.598107] asus_wmi: Number of fans: 1
[   21.653002] init: failsafe main process (1298) killed by TERM signal
[   21.669598] cfg80211: World regulatory domain updated:
[   21.669603] cfg80211:  DFS Master region: unset
[   21.669605] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   21.669609] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   21.669612] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   21.669615] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   21.669618] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   21.669621] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   22.251663] init: alsa-restore main process (1673) terminated with status 99
[   22.516330] r8169 0000:02:00.0 eth0: link down
[   22.516516] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.563206] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.270381] init: plymouth-upstart-bridge main process ended, respawning
[   24.276158] init: plymouth-upstart-bridge main process (2031) terminated with status 1
[   24.276173] init: plymouth-upstart-bridge main process ended, respawning
[   26.619534] usb 1-4: New USB device found, idVendor=13d3, idProduct=3402
[   26.619541] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   26.619545] usb 1-4: Product: Bluetooth USB Host Controller
[   26.619548] usb 1-4: Manufacturer: Atheros Communications
[   26.619551] usb 1-4: SerialNumber: Alaska Day 2006
[   29.729036] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   29.729335] ACPI: \_SB_.PCI0.RP05.PEGP: failed to evaluate _DSM
[   29.729340] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   69.722555] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   69.722918] ACPI: \_SB_.PCI0.RP05.PEGP: failed to evaluate _DSM
[   69.722926] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   96.568810] raid6: mmxx1    gen()  3604 MB/s
[   96.636796] raid6: mmxx2    gen()  3682 MB/s
[   96.704776] raid6: sse1x1   gen()  3041 MB/s
[   96.772740] raid6: sse1x2   gen()  3674 MB/s
[   96.840708] raid6: sse2x1   gen()  6181 MB/s
[   96.908691] raid6: sse2x1   xor()  4500 MB/s
[   96.976657] raid6: sse2x2   gen()  7465 MB/s
[   97.044635] raid6: sse2x2   xor()  4928 MB/s
[   97.112610] raid6: avx2x1   gen() 12065 MB/s
[   97.180586] raid6: avx2x2   gen() 13507 MB/s
[   97.180588] raid6: using algorithm avx2x2 gen() 13507 MB/s
[   97.180590] raid6: using avx2x1 recovery algorithm
[   97.186105] xor: automatically using best checksumming function:
[   97.224567]    avx       : 18868.000 MB/sec
[   97.285675] Btrfs loaded
[   97.329345] JFS: nTxBlock = 8192, nTxLock = 65536
[   97.420926] SGI XFS with ACLs, security attributes, realtime, no debug enabled
[  120.768494] ntfs: driver 2.1.32 [Flags: R/O MODULE].
[  120.818879] QNX4 filesystem 0.2.3 registered.


```
> **weatherman2 said:**
> Also, I checked the support page from Asus.  There is a slightly newer BIOS (version 211) available from Asus, though their note says nothing about fixing a problem like you describe.  But sometimes problems are fixed in a BIOS that aren't noted in the release notes.

I already updated to latest version, still same issue.

---

### Post by oldfred on 2016-08-01
Major issues seem related to AHCI and RAID.

Some older perhaps similar models need boot parameter:
 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)
[http://ubuntuforums.org/showthread.php?t=2327570](http://ubuntuforums.org/showthread.php?t=2327570)
Installing 15.04 on Asus N550JX, boot parameters required
[http://ubuntuforums.org/showthread.php?t=2293394](http://ubuntuforums.org/showthread.php?t=2293394)
Asus ROG G75VW  with Windows 7 in UEFI boot mode.
[http://ubuntuforums.org/showthread.php?t=2251167](http://ubuntuforums.org/showthread.php?t=2251167)
Asus ASUS D550MA-DS01 - 14.04 only Ubuntu
[http://ubuntuforums.org/showthread.php?t=2223928](http://ubuntuforums.org/showthread.php?t=2223928)

---

