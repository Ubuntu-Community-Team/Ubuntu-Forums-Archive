---
title: "Serial USB device's not detected (no event logged), but USB storage device's are ok"
date: 2019-02-25
forum: Hardware
---

### Post by jasonxfield on 2019-02-25
Ok I know this has been a commonly asked question however nothing I have read has helped and I have a different variation of the problem I think from other posts I have read. 

Ubuntu 18.04.2 LTS (64-bit)

kernel: 4.19.1-041901-generic

Firstly : USB storage devices are detected with no problems.
My Problem is any other USB device (serial etc) are not detected at all.  It is hard to determine why as nothing is being registered with dmesg or lsusb output on device connect/disconnect. 

Any help on why this may be happening is appreciated thanks. Ive been trying for days and unfortunately without any event registering in dmesg I really dont know how to begin diagnosing the issue further.

Edit: So basically my question is this - how can debugging Ubuntu USB faults be established when no fault log is registered but obviously USB interface is working (for storage devices) ?

.... Or perhaps the error is there and i just dont understand it.   Several errors occurring towards end of dmesg:

```

[    4.744922] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input27
[    4.745006] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input28
[    4.745083] input: HDA Intel PCH Dock Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input29
[    4.745158] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input30
[    4.745236] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input32
[    4.745309] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input33
[    4.745383] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input34
[    4.770638] RAPL PMU: API unit is 2^-32 Joules, 3 fixed counters, 163840 ms ovfl timer
[    4.770640] RAPL PMU: hw unit of domain pp0-core 2^-16 Joules
[    4.770642] RAPL PMU: hw unit of domain package 2^-16 Joules
[    4.770642] RAPL PMU: hw unit of domain pp1-gpu 2^-16 Joules
[    4.785556] cryptd: max_cpu_qlen set to 1000
[    4.806926] hp_wmi: query 0xd returned error 0x5
[    4.807053] input: HP WMI hotkeys as /devices/virtual/input/input31
[    4.813303] AVX version of gcm_enc/dec engaged.
[    4.813305] AES CTR mode by8 optimization enabled
[    4.956875] kvm: disabled by bios
[    5.023384] gpio_ich: GPIO from 436 to 511 on gpio_ich
[    5.030708] kvm: disabled by bios
[    5.044238] intel_rapl: Found RAPL domain package
[    5.044240] intel_rapl: Found RAPL domain core
[    5.044241] intel_rapl: Found RAPL domain uncore
[    5.083886] iwlwifi 0000:03:00.0 wlo1: renamed from wlan0
[    5.090543] usb-storage 1-1.4.4:1.0: USB Mass Storage device detected
[    5.097175] scsi host6: usb-storage 1-1.4.4:1.0
[    5.097295] usbcore: registered new interface driver usb-storage
[    5.103154] usbcore: registered new interface driver uas
[    5.302252] random: crng init done
[    5.302255] random: 7 urandom warning(s) missed due to ratelimiting
[    5.707632] audit: type=1400 audit(1551141751.750:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/core/4917/usr/lib/snapd/snap-confine" pid=1072 comm="apparmor_parser"
[    5.707638] audit: type=1400 audit(1551141751.750:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/snap/core/4917/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=1072 comm="apparmor_parser"
[    5.708754] audit: type=1400 audit(1551141751.754:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/freshclam" pid=1075 comm="apparmor_parser"
[    5.711982] audit: type=1400 audit(1551141751.754:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=1076 comm="apparmor_parser"
[    5.711987] audit: type=1400 audit(1551141751.754:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=1076 comm="apparmor_parser"
[    5.711990] audit: type=1400 audit(1551141751.754:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=1076 comm="apparmor_parser"
[    5.712843] audit: type=1400 audit(1551141751.758:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=1071 comm="apparmor_parser"
[    5.712848] audit: type=1400 audit(1551141751.758:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1071 comm="apparmor_parser"
[    5.712851] audit: type=1400 audit(1551141751.758:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=1071 comm="apparmor_parser"
[    5.712854] audit: type=1400 audit(1551141751.758:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1071 comm="apparmor_parser"
[    6.115355] scsi 6:0:0:0: Direct-Access     USB      Flash Disk       2.00 PQ: 0 ANSI: 2
[    6.115685] sd 6:0:0:0: Attached scsi generic sg1 type 0
[    6.117470] sd 6:0:0:0: [sdb] 249856 512-byte logical blocks: (128 MB/122 MiB)
[    6.118095] sd 6:0:0:0: [sdb] Write Protect is off
[    6.118098] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    6.118842] sd 6:0:0:0: [sdb] No Caching mode page found
[    6.118847] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    6.142861]  sdb: sdb1
[    6.158989] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    6.252885] usbcore: registered new interface driver btusb
[    6.305194] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.305196] Bluetooth: BNEP filters: protocol multicast
[    6.305201] Bluetooth: BNEP socket layer initialized
[    6.312847] uvcvideo 1-1.3:1.0: Entity type for entity Extension 5 was not initialized!
[    6.312851] uvcvideo 1-1.3:1.0: Entity type for entity Extension 4 was not initialized!
[    6.312853] uvcvideo 1-1.3:1.0: Entity type for entity Processing 3 was not initialized!
[    6.312856] uvcvideo 1-1.3:1.0: Entity type for entity Camera 1 was not initialized!
[    6.313026] input: HP HD Webcam [Fixed]: HP HD Web as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input35
[    6.313131] usbcore: registered new interface driver uvcvideo
[    6.313133] USB Video Class driver (1.1.1)
[    6.348365] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[    6.361377] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[    6.674871] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[    6.762400] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[    7.773717] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[    7.779881] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[    7.834130] e1000e: enp0s25 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[    7.834135] e1000e 0000:00:19.0 enp0s25: 10/100 speed: disabling TSO
[    7.834171] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready
[    7.938869] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[    9.010286] IPv6: ipv6_create_tempaddr: retry temporary address regeneration
[   11.125794] wlo1: authenticate with a4:91:b1:30:44:05
[   11.129151] wlo1: send auth to a4:91:b1:30:44:05 (try 1/3)
[   11.133217] wlo1: authenticated
[   11.133436] wlo1: waiting for beacon from a4:91:b1:30:44:05
[   11.232055] wlo1: associate with a4:91:b1:30:44:05 (try 1/3)
[   11.239422] wlo1: RX AssocResp from a4:91:b1:30:44:05 (capab=0x1411 status=0 aid=1)
[   11.242455] wlo1: associated
[   11.324446] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[   11.566252] bpfilter: Loaded bpfilter_umh pid 2217
[   12.439804] IPv6: ipv6_create_tempaddr: retry temporary address regeneration
[   25.138364] Bluetooth: RFCOMM TTY layer initialized
[   25.138375] Bluetooth: RFCOMM socket layer initialized
[   25.138382] Bluetooth: RFCOMM ver 1.11
[   26.691828] rfkill: input handler disabled
[13730.044719] perf: interrupt took too long (2545 > 2500), lowering kernel.perf_event_max_sample_rate to 78500
[23311.066896] perf: interrupt took too long (3188 > 3181), lowering kernel.perf_event_max_sample_rate to 62500
[36174.432362] perf: interrupt took too long (4023 > 3985), lowering kernel.perf_event_max_sample_rate to 49500
[48701.755242] perf: interrupt took too long (5038 > 5028), lowering kernel.perf_event_max_sample_rate to 39500
[55003.267972] perf: interrupt took too long (6336 > 6297), lowering kernel.perf_event_max_sample_rate to 31500

```

---

### Post by him610 on 2019-02-26
The only error shown is at [    4.806926]
There are several entries relating to USB including a storage device and a blue tooth device.

Please show the results of *dmesg | grep usb*

---

### Post by jasonxfield on 2019-02-26
Thanks him610. 

Output after inserting device (Arduino Micro - microcontroller):
```

dmesg | grep usb
[    0.559601] usbcore: registered new interface driver usbfs
[    0.559601] usbcore: registered new interface driver hub
[    0.560028] usbcore: registered new device driver usb
[    2.300109] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 4.19
[    2.300112] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.300114] usb usb1: Product: EHCI Host Controller
[    2.300116] usb usb1: Manufacturer: Linux 4.19.1-041901-generic ehci_hcd
[    2.300118] usb usb1: SerialNumber: 0000:00:1a.0
[    2.320133] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 4.19
[    2.320135] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.320137] usb usb2: Product: EHCI Host Controller
[    2.320139] usb usb2: Manufacturer: Linux 4.19.1-041901-generic ehci_hcd
[    2.320141] usb usb2: SerialNumber: 0000:00:1d.0
[    2.322134] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 4.19
[    2.322136] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.322138] usb usb3: Product: xHCI Host Controller
[    2.322140] usb usb3: Manufacturer: Linux 4.19.1-041901-generic xhci-hcd
[    2.322142] usb usb3: SerialNumber: 0000:00:14.0
[    2.322932] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 4.19
[    2.322935] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.322936] usb usb4: Product: xHCI Host Controller
[    2.322938] usb usb4: Manufacturer: Linux 4.19.1-041901-generic xhci-hcd
[    2.322940] usb usb4: SerialNumber: 0000:00:14.0
[    2.640052] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.656895] usb 3-1: new high-speed USB device number 2 using xhci_hcd
[    2.664035] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.796419] usb 1-1: New USB device found, idVendor=8087, idProduct=0024, bcdDevice= 0.00
[    2.796421] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.812127] usb 3-1: New USB device found, idVendor=0424, idProduct=2514, bcdDevice= b.b3
[    2.812130] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.824416] usb 2-1: New USB device found, idVendor=8087, idProduct=0024, bcdDevice= 0.00
[    2.824418] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.948027] usb 3-4: new full-speed USB device number 3 using xhci_hcd
[    3.092024] usb 1-1.1: new full-speed USB device number 3 using ehci-pci
[    3.097986] usb 3-4: New USB device found, idVendor=046d, idProduct=c534, bcdDevice=29.01
[    3.097988] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.097990] usb 3-4: Product: USB Receiver
[    3.097992] usb 3-4: Manufacturer: Logitech
[    3.109340] usbcore: registered new interface driver usbhid
[    3.109342] usbhid: USB HID core driver
[    3.112423] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/0003:046D:C534.0001/input/input10
[    3.172443] hid-generic 0003:046D:C534.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:14.0-4/input0
[    3.172765] input: Logitech USB Receiver Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.1/0003:046D:C534.0002/input/input11
[    3.172918] input: Logitech USB Receiver Consumer Control as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.1/0003:046D:C534.0002/input/input12
[    3.202166] usb 1-1.1: New USB device found, idVendor=138a, idProduct=003d, bcdDevice= 1.04
[    3.202168] usb 1-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[    3.202169] usb 1-1.1: SerialNumber: 00207ec5e78d
[    3.232379] input: Logitech USB Receiver System Control as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.1/0003:046D:C534.0002/input/input13
[    3.232660] hid-generic 0003:046D:C534.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:14.0-4/input1
[    3.280133] usb 1-1.2: new full-speed USB device number 4 using ehci-pci
[    3.393216] usb 1-1.2: New USB device found, idVendor=8087, idProduct=07da, bcdDevice=78.69
[    3.393218] usb 1-1.2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.472138] usb 1-1.3: new high-speed USB device number 5 using ehci-pci
[    3.629796] usb 1-1.3: New USB device found, idVendor=04f2, idProduct=b2ef, bcdDevice=51.72
[    3.629799] usb 1-1.3: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    3.629801] usb 1-1.3: Product: HP HD Webcam [Fixed]
[    3.629803] usb 1-1.3: Manufacturer: Chicony Electronics Co., Ltd.
[    3.629805] usb 1-1.3: SerialNumber: SN0001
[    3.712040] usb 1-1.4: new high-speed USB device number 6 using ehci-pci
[    3.824474] usb 1-1.4: New USB device found, idVendor=0424, idProduct=2514, bcdDevice= b.b3
[    3.824476] usb 1-1.4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.116038] usb 1-1.4.1: new full-speed USB device number 7 using ehci-pci
[    4.227293] usb 1-1.4.1: New USB device found, idVendor=046d, idProduct=c534, bcdDevice=29.00
[    4.227297] usb 1-1.4.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.227299] usb 1-1.4.1: Product: USB Receiver
[    4.227301] usb 1-1.4.1: Manufacturer: Logitech
[    4.229205] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4.1/1-1.4.1:1.0/0003:046D:C534.0003/input/input19
[    4.288232] hid-generic 0003:046D:C534.0003: input,hidraw2: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.0-1.4.1/input0
[    4.290951] input: Logitech USB Receiver Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4.1/1-1.4.1:1.1/0003:046D:C534.0004/input/input20
[    4.291125] input: Logitech USB Receiver Consumer Control as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4.1/1-1.4.1:1.1/0003:046D:C534.0004/input/input21
[    4.348263] input: Logitech USB Receiver System Control as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4.1/1-1.4.1:1.1/0003:046D:C534.0004/input/input22
[    4.348429] hid-generic 0003:046D:C534.0004: input,hiddev1,hidraw3: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-1.4.1/input1
[    4.432044] usb 1-1.4.4: new high-speed USB device number 8 using ehci-pci
[    4.543539] usb 1-1.4.4: New USB device found, idVendor=0ea0, idProduct=2168, bcdDevice= 2.00
[    4.543542] usb 1-1.4.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.543544] usb 1-1.4.4: Product: Flash Disk      
[    4.543546] usb 1-1.4.4: Manufacturer: USB     
[    4.610046] usbcore: registered new interface driver btusb
[    5.127308] usb-storage 1-1.4.4:1.0: USB Mass Storage device detected
[    5.129748] scsi host6: usb-storage 1-1.4.4:1.0
[    5.129867] usbcore: registered new interface driver usb-storage
[    5.131986] usbcore: registered new interface driver uas
[    6.449786] input: HP HD Webcam [Fixed]: HP HD Web as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input35
[    6.449941] usbcore: registered new interface driver uvcvideo

```

Doesn't appear to register from what I can see.

---

### Post by jasonxfield on 2019-02-27
Also lshw output: (still nothing ?)

```

sudo lshw   
    description: Notebook
    product: HP EliteBook 2170p (B8J91AW#ABA)
    vendor: Hewlett-Packard
    version: A1029D1102
    serial: 2CE24914W6
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5336AN G=N L=BUS B=HP S=ELI sku=B8J91AW#ABA uuid=370397A2-F53E-E211-862A-92C459008063
  *-core
       description: Motherboard
       product: 1815
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 63.1B
       serial: PDARR1B2E3R0RX
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: e
          version: 68IMT Ver. F.44
          date: 01/10/2014
          size: 64KiB
          capacity: 5056KiB
          capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-3427U CPU @ 1.80GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-3427U CPU @ 1.80GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 2746MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm cpuid_fault epb pti tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 2
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-through instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 3
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 4
             slot: Unknown
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
             configuration: level=3
     *-cache
          description: L1 cache
          physical id: 1
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 5
          slot: System board or motherboard
          size: 12GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 99U5428-018.A00LF
             vendor: Kingston
             physical id: 0
             serial: 51242133
             slot: Bottom-Slot 1(top)
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 16KTF51264HZ-1G6M1
             vendor: Micron
             physical id: 1
             serial: E878EDCB
             slot: Bottom-Slot 2(under)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: 3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=ivb_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:30 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:2000(size=64) memory:c0000-dffff
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:27 memory:d0720000-d072ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.19.1-041901-generic xhci-hcd
                physical id: 0
                bus info: usb@3
                logical name: usb3
                version: 4.19
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
              *-usb:0
                   description: USB hub
                   product: USB 2.0 Hub
                   vendor: Standard Microsystems Corp.
                   physical id: 1
                   bus info: usb@3:1
                   version: b.b3
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=2mA slots=2 speed=480Mbit/s
              *-usb:1
                   description: Keyboard
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 4
                   bus info: usb@3:4
                   version: 29.01
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.19.1-041901-generic xhci-hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.19
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
        *-communication:0
             description: Communication controller
             product: 7 Series/C216 Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:31 memory:d0734000-d073400f
        *-communication:1
             description: Serial controller
             product: 7 Series/C210 Series Chipset Family KT Controller
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:17 ioport:2090(size=8) memory:d073b000-d073bfff
        *-network
             description: Ethernet interface
             product: 82579LM Gigabit Network Connection (Lewisville)
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: enp0s25
             version: 04
             serial: 10:1f:74:77:d3:83
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.15-4 ip=192.168.1.57 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:28 memory:d0700000-d071ffff memory:d073a000-d073afff ioport:2060(size=32)
        *-usb:1
             description: USB controller
             product: 7 Series/C216 Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:d0739000-d07393ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.19.1-041901-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.19
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb:0 UNCLAIMED
                      description: Generic USB device
                      product: VFS491
                      vendor: Validity Sensors, Inc.
                      physical id: 1
                      bus info: usb@1:1.1
                      version: 1.04
                      serial: 00207ec5e78d
                      capabilities: usb-1.10
                      configuration: maxpower=100mA speed=12Mbit/s
                 *-usb:1
                      description: Bluetooth wireless interface
                      vendor: Intel Corp.
                      physical id: 2
                      bus info: usb@1:1.2
                      version: 78.69
                      capabilities: bluetooth usb-2.00
                      configuration: driver=btusb speed=12Mbit/s
                 *-usb:2
                      description: Video
                      product: HP HD Webcam [Fixed]
                      vendor: Chicony Electronics Co., Ltd.
                      physical id: 3
                      bus info: usb@1:1.3
                      version: 51.72
                      serial: SN0001
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
                 *-usb:3
                      description: USB hub
                      product: USB 2.0 Hub
                      vendor: Standard Microsystems Corp.
                      physical id: 4
                      bus info: usb@1:1.4
                      version: b.b3
                      capabilities: usb-2.00
                      configuration: driver=hub maxpower=2mA slots=4 speed=480Mbit/s
                    *-usb:0
                         description: Keyboard
                         product: USB Receiver
                         vendor: Logitech
                         physical id: 1
                         bus info: usb@1:1.4.1
                         version: 29.00
                         capabilities: usb-2.00
                         configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
                    *-usb:1
                         description: Mass storage device
                         product: Flash Disk
                         vendor: USB
                         physical id: 4
                         bus info: usb@1:1.4.4
                         logical name: scsi6
                         version: 2.00
                         capabilities: usb-2.00 scsi emulated scsi-host
                         configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
                       *-disk
                            description: SCSI Disk
                            product: Flash Disk
                            vendor: USB
                            physical id: 0.0.0
                            bus info: scsi@6:0.0.0
                            logical name: /dev/sdb
                            version: 2.00
                            size: 122MiB (127MB)
                            capabilities: removable
                            configuration: ansiversion=2 logicalsectorsize=512 sectorsize=512
                          *-medium
                               physical id: 0
                               logical name: /dev/sdb
                               size: 122MiB (127MB)
                               capabilities: partitioned partitioned:dos
                               configuration: signature=3f3727ab
                             *-volume
                                  description: Windows FAT volume
                                  vendor: MSDOS5.0
                                  physical id: 1
                                  logical name: /dev/sdb1
                                  logical name: /media/xfield/PKBACK
                                  version: FAT16
                                  serial: fa23-6c0d
                                  size: 121MiB
                                  capacity: 121MiB
                                  capabilities: primary bootable fat initialized
                                  configuration: FATs=2 filesystem=fat label=PKBACK mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
        *-multimedia
             description: Audio device
             product: 7 Series/C216 Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:33 memory:d0730000-d0733fff
        *-pci:0
             description: PCI bridge
             product: 7 Series/C216 Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 memory:d0600000-d06fffff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:d0500000-d05fffff
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=sdhci-pci latency=0
                resources: irq:18 memory:d0503000-d05030ff memory:d0510000-d051ffff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:d0502000-d05020ff
        *-pci:2
             description: PCI bridge
             product: 7 Series/C216 Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:d0400000-d04fffff
           *-network
                description: Wireless interface
                product: Centrino Advanced-N 6235
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlo1
                version: 24
                serial: c8:f7:33:3b:8b:d9
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.19.1-041901-generic firmware=18.168.6.1 ip=192.168.1.39 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:32 memory:d0400000-d0401fff
        *-usb:2
             description: USB controller
             product: 7 Series/C216 Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:d0738000-d07383ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.19.1-041901-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.19
                capabilities: usb-2.00
                configuration: driver=hub slots=3 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: QM77 Express Chipset LPC Controller
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
             product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:29 ioport:2088(size=8) ioport:209c(size=4) ioport:2080(size=8) ioport:2098(size=4) ioport:2040(size=32) memory:d0737000-d07377ff
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: CT500MX500SSD1
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 020
             serial: 1816E1380C81
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=e66b09f8
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 59dc5f7f-9a77-4665-9e76-30f6dfad63e7
                size: 298GiB
                capacity: 465GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2018-05-03 11:26:16 filesystem=ext4 lastmountpoint=/ modified=2019-02-27 11:38:20 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2019-02-27 11:36:08 state=mounted
  *-battery
       product: MI06048
       vendor: 12-54
       physical id: 1
       slot: Primary
       capacity: 48840mWh
       configuration: voltage=11.1V

```

---

### Post by him610 on 2019-02-27
Your system certainly does recognize USB items other than storage devices, just maybe not the Arduino Micro. Your USB devices include Keyboard, USB Receiver, Bluetooth wireless interface, HP HD Webcam, and a Flash Disk.

Knowledge concerning the Arduino Micro is beyond my limited technical knowledge. 
After reading the datasheet on Arduino Micro - microcontroller at [http://www.farnell.com/datasheets/1685581.pdf]("http://www.farnell.com/datasheets/1685581.pdf"), It seems to me you might have better luck asking the folks who make the device. Do they not have a Support line, Forum, or FAQs?

It also could be your Arduino Micro is not getting enough power through the USB connector. I gleaned this from the datasheet referenced above, > The board can operate on an external supply of 6 to 20 volts. If supplied with less than 7V, however, the 5V
pin may supply less than five volts and the board may be unstable. If using more than 12V, the voltage
regulator may overheat and damage the board. The recommended range is 7 to 12 volts. 

Good luck.

---

### Post by jasonxfield on 2019-02-27
Unfortunately the problem has not been limited to Arduino microcontrollers, I have the same problem with any smartphone, Ledger Nano S, basically anything I plug in other than computer hardware.  As for Arduino specifically, their documentation states that Linux drivers are not required, however they do provide troubleshooting steps ([https://playground.arduino.cc/Linux/All#Permission](https://playground.arduino.cc/Linux/All#Permission)) if device is not recognised but unfortunately these steps are impossible without having capability of finding the device idVendor and idProduct. If I attempt to create a Udev rule based on what I can establish should be the device id's Udev is not creating the device folder eg. /dev/ttyACMx. Thanks again for support.

---

### Post by jasonxfield on 2019-03-06
Attempt to revert to older stable Kernel - Linux 4.17.5-041705-generic did not fix the problem.

---

### Post by jasonxfield on 2019-03-13
After all this pain my problem ended up being as simple as using a different cable to connect the devices.  LOL.  Solved.

---

