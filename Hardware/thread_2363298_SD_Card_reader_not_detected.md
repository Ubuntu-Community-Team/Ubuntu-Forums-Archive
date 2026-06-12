---
title: "SD Card reader not detected"
date: 2017-06-08
forum: Hardware
---

### Post by antonio-galanti on 2017-06-08
Hey guys,
I've recently bought this ASUS T101HA which isn't that powerful but definitely what I need in terms of compromise between power and portability.
I managed to install ubuntu (first, then I went ubuntu mate) and some additional wifi drivers. I upgraded to the 4.11 kernel and even the bluetooth is recognized correctly.
Unfortunately what's missing is my SD Card reader, which is a deal breaker since I store most of my files ina 128 GB SD card always connected to my device.
Windows sees 2 sd card controllers: one is for the eMMC storage and the other for the actual external sd card. Both of them run generic intel drivers so I have no idea of which manufacturer they're from.[/COLOR]
I'm posting my lshw printout hoping someone can help (Please, I'm kinda desperate! :()
Thanks


P.S.: latest 4.12 kernel won't work and will give me other troubles.

```
antonio-t101ha
    description: Computer
    product: T101HA (ASUS-TabletSKU)
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: GAN0CX041581408
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 vsyscall32
    configuration: boot=normal family=T sku=ASUS-TabletSKU uuid=34189B4E-2D4F-4BFE-A106-15CD9F6F88BE
  *-core
       description: Motherboard
       product: T101HA
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: T101HA.303
          date: 01/24/2017
          size: 64KiB
          capacity: 6080KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR3 1600 MHz (0,6 ns)
             product: Array1_PartNumber0
             vendor: A1_Manufacturer0
             physical id: 0
             serial: A1_SerNum0
             slot: A1_DIMM0
             size: 4GiB
             width: 8 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM [empty]
             product: Array1_PartNumber1
             vendor: A1_Manufacturer1
             physical id: 1
             serial: A1_SerNum1
             slot: A1_DIMM1
     *-cache:0
          description: L1 cache
          physical id: 12
          slot: CPU Internal L1
          size: 224KiB
          capacity: 224KiB
          capabilities: internal write-back
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 13
          slot: CPU Internal L2
          size: 2MiB
          capacity: 2MiB
          capabilities: internal write-back unified
          configuration: level=2
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) x5-Z8350  CPU @ 1.44GHz
          vendor: Intel Corp.
          physical id: 14
          bus info: cpu@0
          version: Intel(R) Atom(TM) x5-Z8350 CPU @ 1.44GHz
          slot: SOCKET 0
          size: 872MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 80MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
          configuration: cores=4 enabledcores=4 threads=4
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 36
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
             version: 36
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:299 memory:90000000-90ffffff memory:80000000-8fffffff ioport:f000(size=64) memory:c0000-dffff
        *-multimedia UNCLAIMED
             description: Multimedia controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: latency=0
             resources: memory:91000000-913fffff
        *-generic:0
             description: Non-VGA unclassified device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel_ish_ipc latency=0
             resources: irq:20 memory:91a3a000-91a3afff
        *-generic:1
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 36
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:306 memory:91a39000-91a39fff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 36
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:298 memory:91a00000-91a0ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.11.0-041100rc8-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.11
                capabilities: usb-2.00
                configuration: driver=hub slots=7 speed=480Mbit/s
              *-usb:0
                   description: Bluetooth wireless interface
                   vendor: IMC Networks
                   physical id: 3
                   bus info: usb@1:3
                   version: 0.01
                   capabilities: bluetooth usb-1.10
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:1
                   description: Keyboard
                   product: ASUS HID Device
                   vendor: ASUS Tech Inc.
                   physical id: 4
                   bus info: usb@1:4
                   version: 0.07
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.11.0-041100rc8-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.11
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic:2
             description: Encryption controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:305 memory:91900000-919fffff memory:91800000-918fffff
        *-pci
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:297 memory:91600000-917fffff
           *-network
                description: Wireless interface
                product: Qualcomm Atheros
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlp1s0
                version: 31
                serial: f0:03:8c:0b:a7:17
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath10k_pci driverversion=4.11.0-041100rc8-generic firmware=WLAN.TF.1.0-00267-1 ip=10.101.0.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:307 memory:91600000-917fffff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0

```

---

### Post by Autodave on 2017-06-08
What happens when you insert the card with the machine booted: does it appear on the desktop?

---

### Post by antonio-galanti on 2017-06-08
Nope, nothing happens... :(

---

### Post by cariboo on 2017-06-10
Could you post the output of dmesg, it should look something like this if it's working:

```
[84423.787450] mmc0: new SD card at address 8001
[84423.790243] mmcblk0: mmc0:8001 SD02G 1.89 GiB (ro)
[84423.796521]  mmcblk0: p1
```

---

### Post by efflandt on 2017-06-11
What file system is on the 128 GB (midro?)SD? The internal slot on your device says it supports **eMMC:** 32GB / 64GB / 128GB EMMC. However by default 64 GB or larger SDXC is formatted with exFAT, so have you installed **exfat-utils** in Ubuntu?

As far as external USB card readers, I have one USB 2.0 multi reader that I got that I hoped would work for CF (for old camera) and microUSB directly. However, its LED does not light up and nothing shows in dmesg or lsusb for it when connected to my main Dell PC from 2010 on USB 2.0. Fortunately the 64 GB microSDXC for my phone in SD adapter works in that PC's internally USB connected card slot (w/exfat-utils installed). I have to leave that microSD formatted as exFAT because even though my Samsung J7 Android 6.0.1 uses ext4 for its internal storage, it refuses to use the microSD formatted ext4.

That USB card reader works fine in Ubuntu 16.04 on much older PC's and laptops including USB 2.0 on one old Dell that has a mix of USB 1.0 and 2.0.

But what I am not clear about is when you say "actual external sd card" are you also trying a USB card reader and does anything show up for it in dmesg or lsusb when it is connected with card inserted? I don't know why that one card reader does not even power up in my main PC when all other USB memory card readers and USB memory sticks work.

---

### Post by Bucky Ball on 2017-06-11
You need to install exfat-tools and exfat-utils to read cards that size. You'll find them in the repositores or install from terminal.

```
sudo apt install exfat-utils exfat-tools
```

Don't know if that's your problem, but even with a working SD reader, you won't read those cards without the above.

Good luck. ;)

* Just noticed this from efflandt:

> so have you installed exfat-utils in Ubuntu?

You need exfat-tools as well AFAIK. ;)

---

### Post by antonio-galanti on 2017-06-15
Sorry guys,
I didn't express myself properly.
I've got an INTEGRATED SD card reader, which is not recognized, with a NTFS formatted 128 GB SD card inside it.
The eMMC, which has two partitions (NTFS for windows and Ext4 for Linux), is fine, I even see it on my desktop.

Here's the output of dmesg command:
[https://paste.ubuntu.com/24863131/](https://paste.ubuntu.com/24863131/)

Thanks everybody for helping!
Antonio

---

### Post by Bucky Ball on 2017-06-15
If you're meaning you have a laptop with a built-in, or integrated, card reader slot - not an external, plug in card reader - and you are shoving the 128Gb SD card in and it can't be seen, then you possibly need exfat-utils and exfat-tools, as mentioned. Larger cards need them. Did you install and try?

It looks like your reader is there from the dmesg, but I'm not expert and cariboo and others can confirm. ;)

---

### Post by skinspacec11 on 2017-06-15
> **bucky ball said:**
> you need to install exfat-tools and exfat-utils to read cards that size. You'll find them in the repositores or install from terminal.

```
sudo apt install exfat-utils exfat-tools
```

don't know if that's your problem, but even with a working sd reader, you won't read those cards without the above.

Good luck. ;)

* just noticed this from efflandt:



You need exfat-tools as well afaik. ;)


i agree with this reply.

---

### Post by antonio-galanti on 2017-06-15
I did try to install exfat-utils and exfat-tools.
The former was already installed, while the latter wasn't found by apt.
Anyway the micro-SD I put in is formatted NTFS, do I still need exfat stuff?
Thanks

---

### Post by Bucky Ball on 2017-06-15
Yep. To see cards that size. 

Sorry. That should be *_exfat-fuse_* and exfat-utils. My mistake. ;)

---

### Post by efflandt on 2017-06-15
Installing exfat-utils installs exfat-fuse to automount exfat, but probably not even necessary if using ntfs and ext4. 

This appears to be the section of dmesg related to your card reader:```

[    2.508530] sdhci: Secure Digital Host Controller Interface driver
[    2.508533] sdhci: Copyright(c) Pierre Ossman
[    2.531260] hidraw: raw HID events driver (C) Jiri Kosina
[    2.536177] mmc0: SDHCI controller on ACPI [80860F14:00] using ADMA
[    2.554026] usb 1-3: new full-speed USB device number 2 using xhci_hcd
[    2.557055] mmc1: SDHCI controller on ACPI [80860F14:03] using ADMA
[    2.570853] wmi: Mapper loaded
[    2.578801] intel_ish_ipc 0000:00:0a.0: enabling device (0000 -> 0002)
[    2.699423] usb 1-3: New USB device found, idVendor=13d3, idProduct=3501
[    2.699442] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.746346] mmc0: new HS200 MMC card at address 0001
[    2.751461] mmcblk0: mmc0:0001 DF4064 58.2 GiB 
[    2.751651] mmcblk0boot0: mmc0:0001 DF4064 partition 1 4.00 MiB
[    2.752084] mmcblk0boot1: mmc0:0001 DF4064 partition 2 4.00 MiB
[    2.752343] mmcblk0rpmb: mmc0:0001 DF4064 partition 3 4.00 MiB
[    2.758798]  mmcblk0: p1 p2 p3 p4 p5
```Ignoring USB related things, it appears to think your SD card is 58.2 GiB. What partitioning are you using msdos or gpt?

I don't have anything with new enough mmc to even use SDHC much less SDXC (just more widely supported internally connected USB card readers). But maybe someone could help if you can identify the (Intel?) eMMC device in output of: sudo lspci -v

---

### Post by antonio-galanti on 2017-06-16
> **Bucky Ball said:**
> Yep. To see cards that size. 

Sorry. That should be *_exfat-fuse_* and exfat-utils. My mistake. ;)

Looks like it's already installed :(

> **efflandt said:**
> Installing exfat-utils installs exfat-fuse to automount exfat, but probably not even necessary if using ntfs and ext4. 

This appears to be the section of dmesg related to your card reader:```

[    2.508530] sdhci: Secure Digital Host Controller Interface driver
[    2.508533] sdhci: Copyright(c) Pierre Ossman
[    2.531260] hidraw: raw HID events driver (C) Jiri Kosina
[    2.536177] mmc0: SDHCI controller on ACPI [80860F14:00] using ADMA
[    2.554026] usb 1-3: new full-speed USB device number 2 using xhci_hcd
[    2.557055] mmc1: SDHCI controller on ACPI [80860F14:03] using ADMA
[    2.570853] wmi: Mapper loaded
[    2.578801] intel_ish_ipc 0000:00:0a.0: enabling device (0000 -> 0002)
[    2.699423] usb 1-3: New USB device found, idVendor=13d3, idProduct=3501
[    2.699442] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.746346] mmc0: new HS200 MMC card at address 0001
[    2.751461] mmcblk0: mmc0:0001 DF4064 58.2 GiB 
[    2.751651] mmcblk0boot0: mmc0:0001 DF4064 partition 1 4.00 MiB
[    2.752084] mmcblk0boot1: mmc0:0001 DF4064 partition 2 4.00 MiB
[    2.752343] mmcblk0rpmb: mmc0:0001 DF4064 partition 3 4.00 MiB
[    2.758798]  mmcblk0: p1 p2 p3 p4 p5
```Ignoring USB related things, it appears to think your SD card is 58.2 GiB. What partitioning are you using msdos or gpt?

I don't have anything with new enough mmc to even use SDHC much less SDXC (just more widely supported internally connected USB card readers). But maybe someone could help if you can identify the (Intel?) eMMC device in output of: sudo lspci -v

I'm afraid it refers to the internal eMMC, which is the actual "disk" of my device, and it's 64 GB.

I'm going to check the partition scheme and tell you!

---

### Post by antonio-galanti on 2017-06-18
> **antonio-galanti said:**
> Looks like it's already installed :(



I'm afraid it refers to the internal eMMC, which is the actual "disk" of my device, and it's 64 GB.

I'm going to check the partition scheme and tell you!

It was MBR. I tried to format it GPT and ExFAT but the device still won't recognize it :(

---

