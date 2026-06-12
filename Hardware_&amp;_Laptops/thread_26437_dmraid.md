---
title: "dmraid"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by jr_G-man on 2005-04-12
I'm trying to connect to an existing RAID 0 setup on my built-in controller (Promise Fastrak100, I think).  I know this is not the preferred method, but a lot of my data is there, and I would really like to get at it.

I understand that 'dmraid' is the tool that I should be utilizing...but, it's not installed on my system...and I cannot find it via apt-get.

I found this thread:  [http://ubuntuforums.org/showthread.php?t=2557](http://ubuntuforums.org/showthread.php?t=2557) which gives detailed instruction on how to compile and set up on a 'warty' box.

I followed the instructions here:  [http://www.ubuntulinux.org/wiki/KernelHowto](http://www.ubuntulinux.org/wiki/KernelHowto) and got all the appropriate kernel sources...even though I think I didn't really need them.

However, when I go to compile dmraid, I get the following:

```
gure@ubuntu:~/dmraid/1.0.0.rc7$ sudo make install
Password:
make -C lib
make[1]: Entering directory `/home/gure/dmraid/1.0.0.rc7/lib'
gcc -MM -MF activate/devmapper.d -I. -I../include -I../lib -O2 -DDMRAID_NATIVE_LOG -DHAVE_GETOPTLONG -fPIC -Wall -Wundef -Wcast-align -Wwrite-strings -Winline -Wshadow -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -DDMRAID_TEST -O2 -D_LARGEFILE64_SOURCE activate/devmapper.c; \
gcc -c -I. -I../include -I../lib -O2 -DDMRAID_NATIVE_LOG -DHAVE_GETOPTLONG -fPIC -Wall -Wundef -Wcast-align -Wwrite-strings -Winline -Wshadow -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -DDMRAID_TEST -O2 -D_LARGEFILE64_SOURCE activate/devmapper.c -o activate/devmapper.o
activate/devmapper.c:12:26: libdevmapper.h: No such file or directory
activate/devmapper.c: In function `mkdm_path':
activate/devmapper.c:29: warning: implicit declaration of function `dm_dir'
activate/devmapper.c:29: warning: initialization makes pointer from integer without a cast
activate/devmapper.c: In function `_init_dm':
activate/devmapper.c:49: warning: implicit declaration of function `dm_log_init'
activate/devmapper.c: At top level:
activate/devmapper.c:53: warning: `struct dm_task' declared inside parameter list
activate/devmapper.c:53: warning: its scope is only this definition or declaration, which is probably not what you want
activate/devmapper.c: In function `_exit_dm':
activate/devmapper.c:56: warning: implicit declaration of function `dm_task_destroy'
activate/devmapper.c:58: warning: implicit declaration of function `dm_lib_release'
activate/devmapper.c:59: warning: implicit declaration of function `dm_lib_exit'
activate/devmapper.c: In function `get_target_list':
activate/devmapper.c:72: warning: implicit declaration of function `dm_task_create'
activate/devmapper.c:72: error: `DM_DEVICE_LIST_VERSIONS' undeclared (first use in this function)
activate/devmapper.c:72: error: (Each undeclared identifier is reported only once
activate/devmapper.c:72: error: for each function it appears in.)
activate/devmapper.c:72: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:73: warning: implicit declaration of function `dm_task_run'
activate/devmapper.c:74: warning: implicit declaration of function `dm_task_get_versions'
activate/devmapper.c:74: warning: pointer/integer type mismatch in conditional expression
activate/devmapper.c: In function `valid_ttype':
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:94: error: dereferencing pointer to incomplete type
activate/devmapper.c:98: error: dereferencing pointer to incomplete type
activate/devmapper.c: At top level:
activate/devmapper.c:109: warning: `struct dm_task' declared inside parameter list
activate/devmapper.c: In function `handle_table':
activate/devmapper.c:133: warning: implicit declaration of function `dm_task_add_target'
activate/devmapper.c: At top level:
activate/devmapper.c:141: warning: `struct dm_task' declared inside parameter list
activate/devmapper.c: In function `parse_table':
activate/devmapper.c:143: warning: passing arg 2 of `handle_table' from incompatible pointer type
activate/devmapper.c: In function `dm_create':
activate/devmapper.c:162: error: `DM_DEVICE_CREATE' undeclared (first use in this function)
activate/devmapper.c:162: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:163: warning: implicit declaration of function `dm_task_set_name'
activate/devmapper.c:164: warning: passing arg 2 of `parse_table' from incompatible pointer type
activate/devmapper.c:170: warning: passing arg 1 of `_exit_dm' from incompatible pointer type
activate/devmapper.c: In function `dm_remove':
activate/devmapper.c:184: error: `DM_DEVICE_REMOVE' undeclared (first use in this function)
activate/devmapper.c:184: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:188: warning: passing arg 1 of `_exit_dm' from incompatible pointer type
activate/devmapper.c: In function `dm_status':
activate/devmapper.c:199: error: storage size of `info' isn't known
activate/devmapper.c:204: error: `DM_DEVICE_STATUS' undeclared (first use in this function)
activate/devmapper.c:204: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:207: warning: implicit declaration of function `dm_task_get_info'
activate/devmapper.c:210: warning: passing arg 1 of `_exit_dm' from incompatible pointer type
activate/devmapper.c:199: warning: unused variable `info'
activate/devmapper.c: In function `dm_version':
activate/devmapper.c:226: error: `DM_DEVICE_VERSION' undeclared (first use in this function)
activate/devmapper.c:226: warning: assignment makes pointer from integer without a cast
activate/devmapper.c:228: warning: implicit declaration of function `dm_task_get_driver_version'
activate/devmapper.c:230: warning: passing arg 1 of `_exit_dm' from incompatible pointer type
make[1]: *** [activate/devmapper.o] Error 1
make[1]: Leaving directory `/home/gure/dmraid/1.0.0.rc7/lib'
make: *** [lib] Error 2
gure@ubuntu:~/dmraid/1.0.0.rc7$
```

Though I'm not entirely sure, I think the basis of my problem is that I don't have devmapper installed.  However, when I attempt to 'apt-get' it, I get the following:
```
gure@ubuntu:~/dmraid/1.0.0.rc7$ sudo apt-get install libdevmapper1.00
Reading package lists... Done
Building dependency tree... Done
libdevmapper1.00 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
gure@ubuntu:~/dmraid/1.0.0.rc7$
```

So, I found the rpm for dmraid here:  [http://people.redhat.com/~heinzm/sw/dmraid/rpm/i386/](http://people.redhat.com/~heinzm/sw/dmraid/rpm/i386/)

I ran:
```
sudo alien dmraid-1.0.0.rc7-1.i386.rpm
```
and got 'dmraid_1.0.0.rc7-2_i386.deb'.  I then ran:
```
sudo dpkg -i dmraid_1.0.0.rc7-2_i386.deb
```
and it appeared to install.

but...trying to run it yields:
```
gure@ubuntu:~/dmraid/1.0.0.rc7$ dmraid
dmraid: error while loading shared libraries: libdevmapper.so.1.01: cannot open shared object file: No such file or directory
gure@ubuntu:~/dmraid/1.0.0.rc7$

```


So...I'm afraid I'm at a loss for this one.  Can anybody help me solve my RAID problem...and/or show me the light with dmraid?


Thanks.



PS.  If it helps, here is my 'dmesg'


```
gure@ubuntu:~/dmraid/1.0.0.rc7$ dmesg
ffer I/O error on device hdk1, logical block 234452355
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452419, sector=234452419
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452419, sector=234452419
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452419, sector=234452419
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452419, sector=234452419
ide: failed opcode was: unknown
PDC202XX: Secondary channel reset.
ide5: reset: success
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452419, sector=234452419
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452419, sector=234452419
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452419, sector=234452419
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452419, sector=234452419
ide: failed opcode was: unknown
PDC202XX: Secondary channel reset.
ide5: reset: success
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452419, sector=234452419
ide: failed opcode was: unknown
end_request: I/O error, dev hdk, sector 234452419
Buffer I/O error on device hdk1, logical block 234452356
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452420, sector=234452420
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452420, sector=234452420
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452420, sector=234452420
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452420, sector=234452420
ide: failed opcode was: unknown
PDC202XX: Secondary channel reset.
ide5: reset: success
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452420, sector=234452420
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452420, sector=234452420
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452420, sector=234452420
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452420, sector=234452420
ide: failed opcode was: unknown
PDC202XX: Secondary channel reset.
ide5: reset: success
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452420, sector=234452420
ide: failed opcode was: unknown
end_request: I/O error, dev hdk, sector 234452420
Buffer I/O error on device hdk1, logical block 234452357
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452421, sector=234452421
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452421, sector=234452421
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452421, sector=234452421
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452421, sector=234452421
ide: failed opcode was: unknown
PDC202XX: Secondary channel reset.
ide5: reset: success
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452421, sector=234452421
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452421, sector=234452421
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452421, sector=234452421
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452421, sector=234452421
ide: failed opcode was: unknown
PDC202XX: Secondary channel reset.
ide5: reset: success
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452421, sector=234452421
ide: failed opcode was: unknown
end_request: I/O error, dev hdk, sector 234452421
Buffer I/O error on device hdk1, logical block 234452358
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452422, sector=234452422
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452422, sector=234452422
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452422, sector=234452422
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452422, sector=234452422
ide: failed opcode was: unknown
PDC202XX: Secondary channel reset.
ide5: reset: success
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452422, sector=234452422
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452422, sector=234452422
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452422, sector=234452422
ide: failed opcode was: unknown
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452422, sector=234452422
ide: failed opcode was: unknown
PDC202XX: Secondary channel reset.
ide5: reset: success
hdk: task_in_intr: status=0x51 { DriveReady SeekComplete Error }
hdk: task_in_intr: error=0x10 { SectorIdNotFound }, LBAsect=234452422, sector=234452422
ide: failed opcode was: unknown
end_request: I/O error, dev hdk, sector 234452422
Buffer I/O error on device hdk1, logical block 234452359
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected VIA KT400/KT400A/KT600 chipset
agpgart: Maximum main memory to use for agp memory: 816M
agpgart: AGP aperture is 128M @ 0xd0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:10.0: irq 21, io base 0xd800
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:10.1: irq 21, io base 0xdc00
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
uhci_hcd 0000:00:10.2: irq 21, io base 0xe000
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
usb 1-1: new low speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
ehci_hcd 0000:00:10.3: irq 21, pci mem 0xeb008000
ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
ehci_hcd 0000:00:10.3: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
usbcore: registered new driver hiddev
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
usbhid: probe of 1-1:1.0 failed with error -5
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
irda_init()
NET: Registered protocol family 23
usb 1-1: USB disconnect, address 2
ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:11.5 to 64
usb 1-1: new low speed USB device using uhci_hcd and address 4
input: USB HID v1.00 Joystick [Gravis Destroyer Tiltpad] on usb-0000:00:10.0-1
usb 1-2: new low speed USB device using uhci_hcd and address 5
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 18
eth0: RealTek RTL8139 at 0xec00, 00:20:ed:62:f5:98, IRQ 18
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.0-2
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
ts: Compaq touchscreen protocol output
usb 3-1: new full speed USB device using uhci_hcd and address 2
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
hub 3-1:1.0: USB hub found
hub 3-1:1.0: 4 ports detected
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.
Fire GL built-in AGP-support
Based on agpgart interface v0.99 (c) Jeff Hartmann
agpgart: Maximum main memory to use for agp memory: 816M
agpgart: Detected a Via Apollo KT400 chipset in AGP v3 mode at 0000:00:00.0
agpgart: AGP aperture is 128M @ 0xd0000000
Power management callback for AGP chipset installed
[fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of chipset)
AGP: Found 2 AGPv3 devices
AGP: Doing enable for AGPv3
agpgart: Found an AGP 3.5 compliant device.
[fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[fglrx] free  AGP = 121909248
[fglrx] max   AGP = 121909248
[fglrx] free  LFB = 108974080
[fglrx] max   LFB = 108974080
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 32768
[fglrx] free  AGP = 121909248
[fglrx] max   AGP = 121909248
[fglrx] free  LFB = 83730432
[fglrx] max   LFB = 83730432
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 32768
eth0: no IPv6 routers present
usb 1-1: hald timed out on ep0in
ibm_acpi: ec object not found
mtrr: no MTRR for d90a7000,1000 found
mtrr: no MTRR for d90a8000,8000 found
mtrr: no MTRR for d90b0000,10000 found
mtrr: no MTRR for d90c0000,40000 found
mtrr: no MTRR for d9100000,100000 found
mtrr: no MTRR for d9200000,200000 found
mtrr: no MTRR for d9400000,400000 found
mtrr: no MTRR for d9800000,100000 found
mtrr: no MTRR for d9900000,80000 found
mtrr: no MTRR for d9980000,40000 found
mtrr: no MTRR for d99c0000,20000 found
mtrr: no MTRR for d99e0000,10000 found
mtrr: no MTRR for d99f0000,8000 found
mtrr: no MTRR for d99f8000,2000 found
mtrr: no MTRR for d99fa000,1000 found
allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.
Fire GL built-in AGP-support
Based on agpgart interface v0.99 (c) Jeff Hartmann
agpgart: Maximum main memory to use for agp memory: 816M
agpgart: Detected a Via Apollo KT400 chipset in AGP v3 mode at 0000:00:00.0
agpgart: AGP aperture is 128M @ 0xd0000000
Power management callback for AGP chipset installed
[fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of chipset)
AGP: Found 2 AGPv3 devices
AGP: Doing enable for AGPv3
agpgart: Found an AGP 3.5 compliant device.
[fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[fglrx] free  AGP = 121909248
[fglrx] max   AGP = 121909248
[fglrx] free  LFB = 116387840
[fglrx] max   LFB = 116387840
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 32768
[fglrx] free  AGP = 121909248
[fglrx] max   AGP = 121909248
[fglrx] free  LFB = 98557952
[fglrx] max   LFB = 98557952
[fglrx] free  Inv = 0
[fglrx] max   Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB  = 0
[fglrx] total AGP = 32768
cdrom: open failed.
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'O', timestamp 2003/09/12 11:19 (1ed4)
i2c /dev entries driver
cdrom: This disc doesn't have any tracks I recognize!
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
gure@ubuntu:~/dmraid/1.0.0.rc7$
```

---

### Post by jr_G-man on 2005-04-13
update...I think I have solved this problem.

I noticed there was another 'libdevmapper' package available.  So, I did:
```
sudo apt-get install libdevmapper-dev
```
and it installed.  I was then able to compile dmraid and I can continue on with the directions.

---

