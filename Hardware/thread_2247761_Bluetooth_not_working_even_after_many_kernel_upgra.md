---
title: "Bluetooth not working even after many kernel upgrades."
date: 2014-10-10
forum: Hardware
---

### Post by sirsachinborkar on 2014-10-10
Hi everyone,
I work on Lenovo ThinkCentre M71z desktop.
I have attached to it a bluetooth dongle which is recognized by the ***lsusb*** command as 
[B]Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
[/B]Ever since I've installed Ubuntu 14.04.1 LTS on this machine, I've not been able to use the aforesaid bluetooth dongle.
I can switch the bluetooth on and off but the bluetooth remains disabled and non-functional. This has been the case even after I've religiously updated my software all the way till date.
I am posting here the results of commands **dmesg, ****lsusb, lshw and lspci commands **below:
Will anybody kindly explain what I can do in order to get my bluetooth dongle working again. (BTW, I am having the same trouble installing my wi-fi dongle, but that story some other time.)

_**dmesg Result -**_
[    0.132638] usbcore: registered new interface driver usbfs
[    0.132644] usbcore: registered new interface driver hub
[    0.132658] usbcore: registered new device driver usb
[    0.876228] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.876230] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.876232] usb usb1: Product: EHCI Host Controller
[    0.876233] usb usb1: Manufacturer: Linux 3.13.0-37-generic ehci_hcd
[    0.876234] usb usb1: SerialNumber: 0000:00:1a.0
[    0.892208] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.892210] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.892211] usb usb2: Product: EHCI Host Controller
[    0.892213] usb usb2: Manufacturer: Linux 3.13.0-37-generic ehci_hcd
[    0.892214] usb usb2: SerialNumber: 0000:00:1d.0
[    1.188222] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.320445] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.320449] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.432128] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.564364] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.564369] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.636080] usb 1-1.1: new high-speed USB device number 3 using ehci-pci
[    1.738296] usb 1-1.1: New USB device found, idVendor=0ac8, idProduct=c444
[    1.738301] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.738304] usb 1-1.1: Product: Integrated Camera
[    1.738306] usb 1-1.1: Manufacturer: Vimicro Corp.
[    1.808048] usb 1-1.2: new full-speed USB device number 4 using ehci-pci
[    1.905748] usb 1-1.2: New USB device found, idVendor=0a12, idProduct=0001
[    1.905750] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.905751] usb 1-1.2: Product: Bluetooth V2.0 Dongle
[    1.905752] usb 1-1.2: Manufacturer: Bluetooth v2.0
[    1.976062] usb 1-1.3: new low-speed USB device number 5 using ehci-pci
[    2.071827] usb 1-1.3: New USB device found, idVendor=17ef, idProduct=6019
[    2.071832] usb 1-1.3: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    2.071835] usb 1-1.3: Product: Lenovo Optical USB Mouse
[    2.079385] usbcore: registered new interface driver usbhid
[    2.079387] usbhid: USB HID core driver
[    2.080582] input: Lenovo Optical USB Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input5
[    2.080654] hid-generic 0003:17EF:6019.0001: input,hidraw0: USB HID v1.11 Mouse [Lenovo Optical USB Mouse] on usb-0000:00:1a.0-1.3/input0
[    2.144005] usb 2-1.1: new high-speed USB device number 3 using ehci-pci
[    2.236988] usb 2-1.1: New USB device found, idVendor=12d1, idProduct=1506
[    2.236993] usb 2-1.1: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[    2.236996] usb 2-1.1: Product: HUAWEI Mobile
[    2.236999] usb 2-1.1: Manufacturer: HUAWEI
[    2.241030] usb-storage 2-1.1:1.4: USB Mass Storage device detected
[    2.241518] scsi4 : usb-storage 2-1.1:1.4
[    2.241585] usb-storage 2-1.1:1.5: USB Mass Storage device detected
[    2.241703] scsi5 : usb-storage 2-1.1:1.5
[    2.241764] usbcore: registered new interface driver usb-storage
[    2.307900] usb 2-1.5: new low-speed USB device number 4 using ehci-pci
[    2.406808] usb 2-1.5: New USB device found, idVendor=04b3, idProduct=3025
[    2.406810] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.406812] usb 2-1.5: Product: USB NetVista Full Width Keyboard.
[    2.406813] usb 2-1.5: Manufacturer: LITE-ON Technology
[    2.411759] input: LITE-ON Technology USB NetVista Full Width Keyboard. as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input6
[    2.411871] hid-generic 0003:04B3:3025.0002: input,hidraw1: USB HID v1.10 Keyboard [LITE-ON Technology USB NetVista Full Width Keyboard.] on usb-0000:00:1d.0-1.5/input0
[    7.801323] usbcore: registered new interface driver btusb
[    8.936402] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input7
[    8.936466] usbcore: registered new interface driver uvcvideo
[    8.936807] usbcore: registered new interface driver usbserial
[    8.936816] usbcore: registered new interface driver usbserial_generic
[    8.936826] usbserial: USB Serial support registered for generic
[    9.110441] usbcore: registered new interface driver cdc_ncm
[    9.154408] usbcore: registered new interface driver cdc_wdm
[    9.171608] huawei_cdc_ncm 2-1.1:1.1 wwan0: register 'huawei_cdc_ncm' at usb-0000:00:1d.0-1.1, Huawei CDC NCM device, 58:2c:80:13:92:63
[    9.171628] usbcore: registered new interface driver huawei_cdc_ncm
[    9.308750] usbcore: registered new interface driver option
[    9.308763] usbserial: USB Serial support registered for GSM modem (1-port)
[    9.308933] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
[    9.308995] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[    9.309038] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB2
[   15.762092] option1 ttyUSB0: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[   15.762104] option1 ttyUSB0: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[   15.762107] option1 ttyUSB0: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[   17.175677] huawei_cdc_ncm 2-1.1:1.1 wwan0: unregister 'huawei_cdc_ncm' usb-0000:00:1d.0-1.1, Huawei CDC NCM device
[   17.191748] option1 ttyUSB2: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[   17.191752] option1 ttyUSB2: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[   17.191754] option1 ttyUSB2: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[   17.267137] usb 2-1.1: reset high-speed USB device number 3 using ehci-pci
[   17.361294] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
[   17.363132] huawei_cdc_ncm 2-1.1:1.1 wwan0: register 'huawei_cdc_ncm' at usb-0000:00:1d.0-1.1, Huawei CDC NCM device, 58:2c:80:13:92:63
[   17.363441] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[   17.363525] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB2
[ 6972.575241] usb 2-1.6: new high-speed USB device number 5 using ehci-pci
[ 6972.669546] usb 2-1.6: New USB device found, idVendor=03f0, idProduct=5607
[ 6972.669550] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 6972.669553] usb 2-1.6: Product: v210w
[ 6972.669556] usb 2-1.6: Manufacturer: HP
[ 6972.669558] usb 2-1.6: SerialNumber: AA00000000006158
[ 6972.669983] usb-storage 2-1.6:1.0: USB Mass Storage device detected
[ 6972.670155] scsi6 : usb-storage 2-1.6:1.0


_**lsusb Result -**_
Bus 002 Device 005: ID 03f0:5607 Hewlett-Packard 
Bus 002 Device 004: ID 04b3:3025 IBM Corp. NetVista Full Width Keyboard
Bus 002 Device 003: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 17ef:6019 Lenovo 
Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 003: ID 0ac8:c444 Z-Star Microelectronics Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


_**lshw Result- **_
sachin-thinkcentre-m71z
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3801MiB
     *-cpu
          product: Intel(R) Core(TM) i5-2500S CPU @ 2.70GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:fe000000-fe3fffff memory:d0000000-dfffffff ioport:f000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:44 memory:fe508000-fe50800f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:17 memory:fe507000-fe5073ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:fe500000-fe503fff
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fe400000-fe4fffff ioport:e0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 06
                serial: f8:0f:41:42:35:4b
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=172.1.0.248 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:42 ioport:e000(size=256) memory:fe400000-fe400fff memory:e0000000-e0003fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fe506000-fe5063ff
        *-isa
             description: ISA bridge
             product: H61 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:fe505000-fe5057ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe504000-fe5040ff ioport:f040(size=32)
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RW DS8A8SH
             vendor: PLDS
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: KL31
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-scsi:0
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@5
       logical name: scsi5
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:2
       physical id: 3
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: wwan0
       serial: 58:2c:80:13:92:63
       capabilities: ethernet physical
       configuration: broadcast=yes driver=huawei_cdc_ncm driverversion=22-Aug-2005 firmware=Huawei CDC NCM device link=no multicast=yes


sachin-thinkcentre-m71z
    description: Desktop Computer
    product: 1782AA9 (To be filled by O.E.M.)
    vendor: LENOVO
    version: ThinkCentre M71z
    serial: L90CA88
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=To be filled by O.E.M. keyboard_password=enabled power-on_password=disabled sku=To be filled by O.E.M. uuid=31F72D1C-302A-2DA8-331E-2DD81C4D2E04
  *-core
       description: Motherboard
       product: To be filled by O.E.M.
       vendor: LENOVO
       physical id: 0
       version: To be filled by O.E.M.
       serial: INVALID
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 9PKT27AUS
          date: 11/01/2011
          size: 64KiB
          capacity: 2496KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: RMT3020EC58E9F1333
             vendor: Undefined
             physical id: 0
             serial: 43F9A42C
             slot: A1_DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber1
             vendor: A1_Manufacturer1
             physical id: 1
             serial: A1_SerNum1
             slot: A1_DIMM1
             width: 64 bits
     *-cache:0
          description: L1 cache
          physical id: 4
          size: 256KiB
          capacity: 256KiB
          capabilities: internal varies
     *-cache:1
          description: L2 cache
          physical id: 5
          size: 1MiB
          capacity: 1MiB
          capabilities: internal varies unified
     *-cache:2
          description: L3 cache
          physical id: 6
          size: 6MiB
          capacity: 6MiB
          capabilities: internal varies unified
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2500S CPU @ 2.70GHz
          vendor: Intel Corp.
          physical id: 17
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-2500S CPU @ 2.70GHz
          slot: SOCKET 0
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=1
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:fe000000-fe3fffff memory:d0000000-dfffffff ioport:f000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:44 memory:fe508000-fe50800f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:17 memory:fe507000-fe5073ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:fe500000-fe503fff
        *-pci:0
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:fe400000-fe4fffff ioport:e0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: eth0
                version: 06
                serial: f8:0f:41:42:35:4b
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=172.1.0.248 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:42 ioport:e000(size=256) memory:fe400000-fe400fff memory:e0000000-e0003fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:fe506000-fe5063ff
        *-isa
             description: ISA bridge
             product: H61 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:fe505000-fe5057ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe504000-fe5040ff ioport:f040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RW DS8A8SH
             vendor: PLDS
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: KL31
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST500DM002-1BD14
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: KC65
             serial: Z2AXZ687
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=0001c623
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: d011687c-3004-4546-b3a4-798a22bfc976
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2013-10-12 03:45:38 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                logical name: /media/sachin/1AF65ECAF65EA633
                version: 3.1
                serial: ee72948e-b351-8a44-9c35-71e162a5fc41
                size: 99GiB
                capacity: 99GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2014-09-06 04:53:14 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: ac8ac9c5-8ce6-6546-a682-d6a3f6e462f5
                size: 199GiB
                capacity: 200GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2013-10-12 03:46:26 filesystem=ntfs state=clean
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@1:0.0.0,4
                logical name: /dev/sda4
                size: 165GiB
                capacity: 165GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3905MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /
                   capacity: 161GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:2
          physical id: 3
          bus info: usb@2:1.1
          logical name: scsi4
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: SCSI CD-ROM
             physical id: 0
             bus info: scsi@4:0.0.0
             logical name: /dev/sr1
             logical name: /media/sachin/Mobile Partner
             capabilities: audio partitioned partitioned:mac
             configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
           *-volume:0 UNCLAIMED
                description: Apple partition map
                physical id: 1
                bus info: scsi@4:0.0.0,1
                capacity: 1KiB
           *-volume:1 UNCLAIMED
                description: Apple HFS
                physical id: 2
                bus info: scsi@4:0.0.0,2
                version: 4
                serial: 00000000-0000-0000-0000-000000001800
                size: 68MiB
                capacity: 68MiB
                capabilities: hfsplus initialized
                configuration: checked=2012-03-22 17:51:29 created=2012-03-22 12:21:29 filesystem=hfsplus lastmountedby=LSDf modified=2012-03-22 17:51:37 state=unclean
        *-disk
             description: SCSI Disk
             physical id: 1
             bus info: scsi@5:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
     *-scsi:3
          physical id: 7
          bus info: usb@2:1.6
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
             size: 7788MiB (8166MB)
             capabilities: partitioned partitioned:dos
             configuration: sectorsize=512 signature=c3072e18
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/sachin/SACHIN
                version: FAT32
                serial: aa5c-0cd0
                size: 7777MiB
                capacity: 7783MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wwan0
       serial: 58:2c:80:13:92:63
       capabilities: ethernet physical
       configuration: broadcast=yes driver=huawei_cdc_ncm driverversion=22-Aug-2005 firmware=Huawei CDC NCM device link=no multicast=yes




_**lspci Result**_
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)

---

