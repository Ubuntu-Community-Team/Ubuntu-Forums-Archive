---
title: "Choppy mouse movement in Ubuntu 8.04"
date: 2008-08-02
forum: Hardware
---

### Post by dustman on 2008-08-02
Hello!

I recently installed Ubuntu 8.04 Hardy Heron, after having sound issues with Gutsy. Everything was working fine, but soon i realized that the mouse movement was very laggy and choppy when i did stuff like starting firefox, nautilus, system monitor and about every program i have installed. The cursor movement if i use the touchpad is smooth though (when the mouse movement started to be choopy, i tried to move the cursor with the touchpad, and it worked ok). I have to mention that i have "irqpoll" as a kernel boot parameter, because the mouse stops working after a few minutes after startup if "irqpoll" is missing there. Has anyone had this problem? Or maybe you know how i can get it fixed? My mouse is a Logitech Premium Optical Wheel Mouse (written on the bottom of the mouse :D).

Thanks in advance!


Cheers,

Radu

---

### Post by rogier.de.groot on 2008-08-02
Any error messages in /var/log/messages? Right video card drivers installed?

---

### Post by dustman on 2008-08-02
Well, there are a lot of: 
```
ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
```

I have an ATI Radeon Xpress 200M video card, with ATI fglrx driver installed. I not into desktop effects, so i guess the default driver that ships with ubuntu will do just fine. Should i disable the proprietary driver?
A glimpse of /var/log/messages:

```
Aug  1 22:57:39 dustman-laptop kernel: [   44.143443] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
Aug  1 22:57:39 dustman-laptop kernel: [   44.736877] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
Aug  1 22:57:39 dustman-laptop kernel: [   44.764315] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
Aug  1 22:57:39 dustman-laptop kernel: [   45.405206] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:16/LNXVIDEO:00/input/input7
Aug  1 22:57:39 dustman-laptop kernel: [   45.436751] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Aug  1 22:57:39 dustman-laptop kernel: [   45.646209] usbcore: registered new interface driver libusual
Aug  1 22:57:39 dustman-laptop kernel: [   45.661850] usbcore: registered new interface driver hiddev
Aug  1 22:57:39 dustman-laptop kernel: [   45.667566] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.0/input/input8
Aug  1 22:57:39 dustman-laptop kernel: [   45.669723] Initializing USB Mass Storage driver...
Aug  1 22:57:39 dustman-laptop kernel: [   45.672818] scsi2 : SCSI emulation for USB Mass Storage devices
Aug  1 22:57:39 dustman-laptop kernel: [   45.692744] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-1
Aug  1 22:57:39 dustman-laptop kernel: [   45.692769] usbcore: registered new interface driver usbhid
Aug  1 22:57:39 dustman-laptop kernel: [   45.692774] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug  1 22:57:39 dustman-laptop kernel: [   45.692914] usbcore: registered new interface driver usb-storage
Aug  1 22:57:39 dustman-laptop kernel: [   45.692918] USB Mass Storage support registered.
Aug  1 22:57:39 dustman-laptop kernel: [   47.166944] cs: IO port probe 0x100-0x3af: clean.
Aug  1 22:57:39 dustman-laptop kernel: [   47.169409] cs: IO port probe 0x3e0-0x4ff: clean.
Aug  1 22:57:39 dustman-laptop kernel: [   47.170437] cs: IO port probe 0x820-0x8ff: clean.
Aug  1 22:57:39 dustman-laptop kernel: [   47.171294] cs: IO port probe 0xc00-0xcf7: clean.
Aug  1 22:57:39 dustman-laptop kernel: [   47.172195] cs: IO port probe 0xa00-0xaff: clean.
Aug  1 22:57:39 dustman-laptop kernel: [   48.100426] ACPI Error (evxfevnt-0383): Could not disable RealTimeClock events [20070126]
Aug  1 22:57:39 dustman-laptop kernel: [   48.212031] lp: driver loaded but no devices found
Aug  1 22:57:39 dustman-laptop kernel: [   48.450718] Adding 996020k swap on /dev/sda3.  Priority:-1 extents:1 across:996020k
Aug  1 22:57:39 dustman-laptop kernel: [   48.926962] EXT3 FS on sda4, internal journal
Aug  1 22:57:39 dustman-laptop kernel: [   49.670370] kjournald starting.  Commit interval 5 seconds
Aug  1 22:57:39 dustman-laptop kernel: [   49.671742] EXT3 FS on sda1, internal journal
Aug  1 22:57:39 dustman-laptop kernel: [   49.671748] EXT3-fs: mounted filesystem with ordered data mode.
Aug  1 22:57:39 dustman-laptop kernel: [   50.298863] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug  1 22:57:39 dustman-laptop kernel: [   50.709694] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-E30N  UE01 PQ: 0 ANSI: 0
Aug  1 22:57:39 dustman-laptop kernel: [   50.710051] scsi 2:0:0:0: Attached scsi generic sg1 type 5
Aug  1 22:57:39 dustman-laptop kernel: [   50.734441] Driver 'sr' needs updating - please use bus_type methods
Aug  1 22:57:39 dustman-laptop kernel: [   50.765920] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Aug  1 22:57:39 dustman-laptop kernel: [   51.290033] No dock devices found.
Aug  1 22:57:39 dustman-laptop kernel: [   52.532194] apm: BIOS not found.
Aug  1 22:57:39 dustman-laptop kernel: [   52.764880] ppdev: user-space parallel port driver
Aug  1 22:57:39 dustman-laptop kernel: [   52.974632] audit(1217620659.874:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5143 profile="/usr/sbin/cupsd" namespace="default"
Aug  1 22:57:40 dustman-laptop dhcdbd: Started up.
Aug  1 22:57:41 dustman-laptop kernel: [   54.142531] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Aug  1 22:57:42 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Aug  1 22:57:42 dustman-laptop kernel: [   55.554390] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 22
Aug  1 22:57:44 dustman-laptop kernel: [   57.387397] NET: Registered protocol family 17
Aug  1 22:57:45 dustman-laptop kernel: [   58.126766] [fglrx] GART Table is not in FRAME_BUFFER range
Aug  1 22:57:45 dustman-laptop kernel: [   58.126782] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Aug  1 22:57:45 dustman-laptop kernel: [   58.126785] [fglrx] Reserve Block - 1 offset =  0Xfff5000 length = 0Xb000
Aug  1 22:57:45 dustman-laptop kernel: [   58.300695] [fglrx] interrupt source 10000000 successfully enabled
Aug  1 22:57:45 dustman-laptop kernel: [   58.300706] [fglrx] enable ID = 0x00000004
Aug  1 22:57:45 dustman-laptop kernel: [   58.301084] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Aug  1 22:57:48 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Aug  1 22:57:48 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Aug  1 22:57:48 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Aug  1 22:57:48 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Aug  1 22:57:49 dustman-laptop kernel: [   62.526165] NET: Registered protocol family 10
Aug  1 22:57:49 dustman-laptop kernel: [   62.526678] lo: Disabled Privacy Extensions
Aug  1 22:57:52 dustman-laptop kernel: [   66.180260] hda-intel: Invalid position buffer, using LPIB read method instead.
Aug  1 22:58:03 dustman-laptop pulseaudio[5739]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug  1 22:58:03 dustman-laptop pulseaudio[5739]: alsa-util.c: Unable to load mixer: No such file or directory
Aug  1 22:58:03 dustman-laptop pulseaudio[5739]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug  1 22:58:03 dustman-laptop pulseaudio[5739]: alsa-util.c: Unable to load mixer: No such file or directory
Aug  1 23:05:03 dustman-laptop kernel: [  497.491578] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  1 23:15:03 dustman-laptop kernel: [ 1097.364509] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  1 23:25:03 dustman-laptop kernel: [ 1697.236533] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  1 23:35:03 dustman-laptop kernel: [ 2297.111657] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  1 23:45:03 dustman-laptop kernel: [ 2897.342494] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  1 23:55:03 dustman-laptop kernel: [ 3496.858283] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 00:05:03 dustman-laptop kernel: [ 4096.741600] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 00:15:03 dustman-laptop kernel: [ 4696.600997] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 00:25:03 dustman-laptop kernel: [ 5296.491882] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 00:35:03 dustman-laptop kernel: [ 5896.346841] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 00:45:03 dustman-laptop kernel: [ 6496.218819] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 00:55:03 dustman-laptop kernel: [ 7096.093705] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 01:05:03 dustman-laptop kernel: [ 7695.971887] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 01:15:03 dustman-laptop kernel: [ 8295.852027] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 01:25:03 dustman-laptop kernel: [ 8895.711698] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 01:31:12 dustman-laptop kernel: [ 9264.719381] usb 3-4: new high speed USB device using ehci_hcd and address 4
Aug  2 01:31:12 dustman-laptop kernel: [ 9264.911046] usb 3-4: configuration #1 chosen from 1 choice
Aug  2 01:31:12 dustman-laptop kernel: [ 9264.962274] scsi3 : SCSI emulation for USB Mass Storage devices
Aug  2 01:31:17 dustman-laptop kernel: [ 9269.954071] usb 3-4: USB disconnect, address 4
Aug  2 01:31:20 dustman-laptop kernel: [ 9273.213666] usb 3-4: new high speed USB device using ehci_hcd and address 5
Aug  2 01:31:20 dustman-laptop kernel: [ 9273.382559] usb 3-4: configuration #1 chosen from 1 choice
Aug  2 01:31:20 dustman-laptop kernel: [ 9273.437702] scsi4 : SCSI emulation for USB Mass Storage devices
Aug  2 01:31:22 dustman-laptop kernel: [ 9275.153510] usb 3-4: USB disconnect, address 5
Aug  2 01:31:24 dustman-laptop kernel: [ 9277.181603] usb 3-3: new high speed USB device using ehci_hcd and address 6
Aug  2 01:31:24 dustman-laptop kernel: [ 9277.369394] usb 3-3: configuration #1 chosen from 1 choice
Aug  2 01:31:24 dustman-laptop kernel: [ 9277.417527] scsi5 : SCSI emulation for USB Mass Storage devices
Aug  2 01:31:29 dustman-laptop kernel: [ 9282.445142] scsi 5:0:0:0: Direct-Access     USB 2.0  Flash Disk       1100 PQ: 0 ANSI: 0 CCS
Aug  2 01:31:30 dustman-laptop kernel: [ 9282.664766] sd 5:0:0:0: [sdb] 3962880 512-byte hardware sectors (2029 MB)
Aug  2 01:31:30 dustman-laptop kernel: [ 9282.712743] sd 5:0:0:0: [sdb] Write Protect is off
Aug  2 01:31:30 dustman-laptop kernel: [ 9282.793000] sd 5:0:0:0: [sdb] 3962880 512-byte hardware sectors (2029 MB)
Aug  2 01:31:30 dustman-laptop kernel: [ 9282.816644] sd 5:0:0:0: [sdb] Write Protect is off
Aug  2 01:31:30 dustman-laptop kernel: [ 9282.816667]  sdb: sdb1
Aug  2 01:31:30 dustman-laptop kernel: [ 9282.898903] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Aug  2 01:31:30 dustman-laptop kernel: [ 9282.898974] sd 5:0:0:0: Attached scsi generic sg2 type 0
Aug  2 01:35:02 dustman-laptop kernel: [ 9495.582571] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 01:45:02 dustman-laptop kernel: [10095.453295] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 01:55:02 dustman-laptop kernel: [10695.333809] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 02:05:02 dustman-laptop kernel: [11295.204303] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 02:15:02 dustman-laptop kernel: [11895.074530] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 02:20:19 dustman-laptop kernel: [12212.296459] usb 3-3: USB disconnect, address 6
Aug  2 02:25:04 dustman-laptop kernel: [12496.598976] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 02:35:02 dustman-laptop kernel: [13094.826366] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 02:45:02 dustman-laptop kernel: [13694.713652] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 02:54:23 dustman-laptop kernel: [14255.696251] [fglrx] interrupt source 10000000 successfully disabled!
Aug  2 02:54:23 dustman-laptop kernel: [14255.696259] [fglrx] enable ID = 0x00000000
Aug  2 02:54:23 dustman-laptop kernel: [14255.696263] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000004
Aug  2 02:54:25 dustman-laptop kernel: [14257.980907] ACPI Error (evxfevnt-0383): Could not disable RealTimeClock events [20070126]
Aug  2 02:54:26 dustman-laptop kernel: [14258.930737] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug  2 02:54:27 dustman-laptop kernel: [14260.015306] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x00a90000
Aug  2 02:54:29 dustman-laptop exiting on signal 15
Aug  2 02:56:15 dustman-laptop syslogd 1.5.0#1ubuntu1: restart.
Aug  2 02:56:16 dustman-laptop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug  2 02:56:16 dustman-laptop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug  2 02:56:16 dustman-laptop kernel: Symbols match kernel version 2.6.24.
Aug  2 02:56:17 dustman-laptop kernel: Loaded 24027 symbols from 91 modules.
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000004fea0000 (usable)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]  BIOS-e820: 000000004fea0000 - 000000004feb0000 (ACPI data)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]  BIOS-e820: 000000004feb0000 - 000000004ff00000 (ACPI NVS)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]  BIOS-e820: 000000004ff00000 - 0000000050000000 (reserved)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] 382MB HIGHMEM available.
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] 896MB LOWMEM available.
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] found SMP MP-table at 000f7630
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Zone PFN ranges:
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]   DMA             0 ->     4096
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]   HighMem    229376 ->   327328
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Movable zone start PFN for each node
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]     0:        0 ->   327328
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] DMI present.
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F75E0 checksum 0
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: RSDP 000F75E0, 0014 (r0 TOSINV)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: RSDT 4FEAAAE6, 0038 (r1 TOSINV   RSDT    6040000  LTP        0)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: FACP 4FEAFEF6, 0074 (r1 TOSINV Goldfish  6040000 ATI     F4240)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: DSDT 4FEAAF3A, 4FBC (r1 TOSINV    SB450  6040000 MSFT  100000E)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: FACS 4FEB0FC0, 0040
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: APIC 4FEAFF6A, 005A (r1 TOSINV ^I APIC    6040000  LTP        0)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: MCFG 4FEAFFC4, 003C (r1 TOSINV   MCFG    6040000  LTP        0)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: SSDT 4FEAAD19, 0221 (r1 TOSINV  Cpu0Cst     3001 INTL 20030224)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: SSDT 4FEAAB1E, 01FB (r1 TOSINV    CpuPm     3000 INTL 20030224)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: DMI detected: Toshiba
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Processor #0 6:13 APIC version 20
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Using ACPI for processor (LAPIC) configuration information
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Intel MultiProcessor Specification v1.4
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000]     Virtual Wire compatibility mode.
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] OEM ID:   Product ID: RS400 Board APIC at: 0xFEE00000
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] I/O APIC #1 Version 33 at 0xFEC00000.
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Processors: 1
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:90000000)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324771
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Kernel command line: root=UUID=3a20c981-7908-4a4a-b830-011f73b58c49 ro noapic irqpoll quiet splash
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Misrouted IRQ fixup and polling support enabled
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] This may significantly impact system performance
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Initializing CPU#0
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug  2 02:56:17 dustman-laptop kernel: [    0.000000] Detected 1592.526 MHz processor.
Aug  2 02:56:17 dustman-laptop kernel: [   27.953639] Console: colour VGA+ 80x25
Aug  2 02:56:17 dustman-laptop kernel: [   27.953644] console [tty0] enabled
Aug  2 02:56:17 dustman-laptop kernel: [   27.954607] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug  2 02:56:17 dustman-laptop kernel: [   27.955452] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug  2 02:56:17 dustman-laptop kernel: [   28.017075] Memory: 1285564k/1309312k available (2177k kernel code, 22492k reserved, 1006k data, 368k init, 391808k highmem)
Aug  2 02:56:17 dustman-laptop kernel: [   28.017086] virtual kernel memory layout:
Aug  2 02:56:17 dustman-laptop kernel: [   28.017087]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug  2 02:56:17 dustman-laptop kernel: [   28.017089]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug  2 02:56:17 dustman-laptop kernel: [   28.017090]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug  2 02:56:17 dustman-laptop kernel: [   28.017091]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug  2 02:56:17 dustman-laptop kernel: [   28.017093]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug  2 02:56:17 dustman-laptop kernel: [   28.017094]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug  2 02:56:17 dustman-laptop kernel: [   28.017095]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug  2 02:56:17 dustman-laptop kernel: [   28.017099] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug  2 02:56:17 dustman-laptop kernel: [   28.017186] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Aug  2 02:56:17 dustman-laptop kernel: [   28.097243] Calibrating delay using timer specific routine.. 3197.85 BogoMIPS (lpj=6395700)
Aug  2 02:56:17 dustman-laptop kernel: [   28.097297] Security Framework initialized
Aug  2 02:56:17 dustman-laptop kernel: [   28.097314] SELinux:  Disabled at boot.
Aug  2 02:56:17 dustman-laptop kernel: [   28.097340] AppArmor: AppArmor initialized
Aug  2 02:56:17 dustman-laptop kernel: [   28.097345] Failure registering capabilities with primary security module.
Aug  2 02:56:17 dustman-laptop kernel: [   28.097357] Mount-cache hash table entries: 512
Aug  2 02:56:17 dustman-laptop kernel: [   28.097571] Initializing cgroup subsys ns
Aug  2 02:56:17 dustman-laptop kernel: [   28.097581] Initializing cgroup subsys cpuacct
Aug  2 02:56:17 dustman-laptop kernel: [   28.097612] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  2 02:56:17 dustman-laptop kernel: [   28.097615] CPU: L2 cache: 1024K
Aug  2 02:56:17 dustman-laptop kernel: [   28.097633] Compat vDSO mapped to ffffe000.
Aug  2 02:56:17 dustman-laptop kernel: [   28.097653] Checking 'hlt' instruction... OK.
Aug  2 02:56:17 dustman-laptop kernel: [   28.113717] SMP alternatives: switching to UP code
Aug  2 02:56:17 dustman-laptop kernel: [   28.115873] Freeing SMP alternatives: 11k freed
Aug  2 02:56:17 dustman-laptop kernel: [   28.116019] Early unpacking initramfs... done
Aug  2 02:56:17 dustman-laptop kernel: [   28.504296] ACPI: Core revision 20070126
Aug  2 02:56:17 dustman-laptop kernel: [   28.504376] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug  2 02:56:17 dustman-laptop kernel: [   28.506405] ACPI: setting ELCR to 0200 (from 0800)
Aug  2 02:56:17 dustman-laptop kernel: [   28.518947] CPU0: Intel(R) Celeron(R) M processor         1.60GHz stepping 08
Aug  2 02:56:17 dustman-laptop kernel: [   28.518975] Total of 1 processors activated (3197.85 BogoMIPS).
Aug  2 02:56:17 dustman-laptop kernel: [   28.625279] Brought up 1 CPUs
Aug  2 02:56:17 dustman-laptop kernel: [   28.625493] net_namespace: 64 bytes
Aug  2 02:56:17 dustman-laptop kernel: [   28.625502] Booting paravirtualized kernel on bare hardware
Aug  2 02:56:17 dustman-laptop kernel: [   28.626014] Time: 23:55:35  Date: 08/01/08
Aug  2 02:56:17 dustman-laptop kernel: [   28.626045] NET: Registered protocol family 16
Aug  2 02:56:17 dustman-laptop kernel: [   28.626254] EISA bus registered
Aug  2 02:56:17 dustman-laptop kernel: [   28.626304] ACPI: bus type pci registered
Aug  2 02:56:17 dustman-laptop kernel: [   28.626580] PCI: PCI BIOS revision 2.10 entry at 0xfd82c, last bus=4
Aug  2 02:56:17 dustman-laptop kernel: [   28.626583] PCI: Using configuration type 1
Aug  2 02:56:17 dustman-laptop kernel: [   28.626593] Setting up standard PCI resources
Aug  2 02:56:17 dustman-laptop kernel: [   28.638986] ACPI: Interpreter enabled
Aug  2 02:56:17 dustman-laptop kernel: [   28.638990] ACPI: (supports S0 S3 S4 S5)
Aug  2 02:56:17 dustman-laptop kernel: [   28.639004] ACPI: Using PIC for interrupt routing
Aug  2 02:56:17 dustman-laptop kernel: [   28.639693] ACPI: EC: non-query interrupt received, switching to interrupt mode
Aug  2 02:56:17 dustman-laptop kernel: [   28.692955] ACPI: EC: GPE = 0x7, I/O: command/status = 0x66, data = 0x62
Aug  2 02:56:17 dustman-laptop kernel: [   28.692959] ACPI: EC: driver started in interrupt mode
Aug  2 02:56:17 dustman-laptop kernel: [   28.693000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug  2 02:56:17 dustman-laptop kernel: [   28.694872] PCI: Transparent bridge - 0000:00:14.4
Aug  2 02:56:17 dustman-laptop kernel: [   28.697248] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
Aug  2 02:56:17 dustman-laptop kernel: [   28.697361] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
Aug  2 02:56:17 dustman-laptop kernel: [   28.697469] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
Aug  2 02:56:17 dustman-laptop kernel: [   28.697578] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)
Aug  2 02:56:17 dustman-laptop kernel: [   28.697686] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 *11)
Aug  2 02:56:17 dustman-laptop kernel: [   28.697794] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
Aug  2 02:56:17 dustman-laptop kernel: [   28.697902] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 *11)
Aug  2 02:56:17 dustman-laptop kernel: [   28.698010] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
Aug  2 02:56:17 dustman-laptop kernel: [   28.698132] ACPI: Power Resource [PFA1] (off)
Aug  2 02:56:17 dustman-laptop kernel: [   28.698181] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug  2 02:56:17 dustman-laptop kernel: [   28.698216] pnp: PnP ACPI init
Aug  2 02:56:17 dustman-laptop kernel: [   28.698224] ACPI: bus type pnp registered
Aug  2 02:56:17 dustman-laptop kernel: [   28.715327] pnp: PnP ACPI: found 10 devices
Aug  2 02:56:17 dustman-laptop kernel: [   28.715329] ACPI: ACPI bus type pnp unregistered
Aug  2 02:56:17 dustman-laptop kernel: [   28.715334] PnPBIOS: Disabled by ACPI PNP
Aug  2 02:56:17 dustman-laptop kernel: [   28.715567] PCI: Using ACPI for IRQ routing
Aug  2 02:56:17 dustman-laptop kernel: [   28.715570] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug  2 02:56:17 dustman-laptop kernel: [   28.741235] NET: Registered protocol family 8
Aug  2 02:56:17 dustman-laptop kernel: [   28.741237] NET: Registered protocol family 20
Aug  2 02:56:17 dustman-laptop kernel: [   28.741313] AppArmor: AppArmor Filesystem Enabled
Aug  2 02:56:17 dustman-laptop kernel: [   28.745226] Time: tsc clocksource has been installed.
Aug  2 02:56:17 dustman-laptop kernel: [   28.753266] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753275] system 00:08: ioport range 0x1080-0x1080 has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753278] system 00:08: ioport range 0x220-0x22f has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753281] system 00:08: ioport range 0x400-0x401 has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753284] system 00:08: ioport range 0x40b-0x40b has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753287] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753290] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753293] system 00:08: ioport range 0x530-0x537 has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753296] system 00:08: ioport range 0xc00-0xc01 has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753299] system 00:08: ioport range 0xc14-0xc14 has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753302] system 00:08: ioport range 0xc50-0xc52 has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753305] system 00:08: ioport range 0xc6c-0xc6c has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753308] system 00:08: ioport range 0xc6f-0xc6f has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753311] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753314] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753317] system 00:08: ioport range 0xcd8-0xcdf has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753320] system 00:08: ioport range 0x8000-0x805f has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753323] system 00:08: ioport range 0xf40-0xf47 has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753326] system 00:08: ioport range 0x280-0x293 has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753329] system 00:08: ioport range 0x87f-0x87f has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753335] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753339] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753342] system 00:09: iomem range 0x0-0xfff could not be reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.753345] system 00:09: iomem range 0xc0004800-0xc0004fff has been reserved
Aug  2 02:56:17 dustman-laptop kernel: [   28.783790] PCI: Bridge: 0000:00:01.0
Aug  2 02:56:17 dustman-laptop kernel: [   28.783793]   IO window: 9000-9fff
Aug  2 02:56:17 dustman-laptop kernel: [   28.783797]   MEM window: c0100000-c01fffff
Aug  2 02:56:17 dustman-laptop kernel: [   28.783801]   PREFETCH window: d0000000-dfffffff
Aug  2 02:56:17 dustman-laptop kernel: [   28.783808] PCI: Bus 3, cardbus bridge: 0000:02:06.0
Aug  2 02:56:17 dustman-laptop kernel: [   28.783811]   IO window: 0000a400-0000a4ff
Aug  2 02:56:17 dustman-laptop kernel: [   28.783817]   IO window: 0000a800-0000a8ff
Aug  2 02:56:17 dustman-laptop kernel: [   28.783824]   PREFETCH window: 64000000-67ffffff
Aug  2 02:56:17 dustman-laptop kernel: [   28.783831]   MEM window: 68000000-6bffffff
Aug  2 02:56:17 dustman-laptop kernel: [   28.783837] PCI: Bridge: 0000:00:14.4
Aug  2 02:56:17 dustman-laptop kernel: [   28.783841]   IO window: a000-afff
Aug  2 02:56:17 dustman-laptop kernel: [   28.783849]   MEM window: c0200000-c02fffff
Aug  2 02:56:17 dustman-laptop kernel: [   28.783854]   PREFETCH window: disabled.
Aug  2 02:56:17 dustman-laptop kernel: [   28.783898] PCI: Enabling device 0000:02:06.0 (0004 -> 0007)
Aug  2 02:56:17 dustman-laptop kernel: [   28.784059] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Aug  2 02:56:17 dustman-laptop kernel: [   28.784068] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Aug  2 02:56:17 dustman-laptop kernel: [   28.784087] NET: Registered protocol family 2
Aug  2 02:56:17 dustman-laptop kernel: [   28.821304] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug  2 02:56:17 dustman-laptop kernel: [   28.821606] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug  2 02:56:17 dustman-laptop kernel: [   28.823624] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug  2 02:56:17 dustman-laptop kernel: [   28.824883] TCP: Hash tables configured (established 131072 bind 65536)
Aug  2 02:56:17 dustman-laptop kernel: [   28.824889] TCP reno registered
Aug  2 02:56:17 dustman-laptop kernel: [   28.833465] checking if image is initramfs... it is
Aug  2 02:56:17 dustman-laptop kernel: [   29.639424] Freeing initrd memory: 7305k freed
Aug  2 02:56:17 dustman-laptop kernel: [   29.640232] audit: initializing netlink socket (disabled)
Aug  2 02:56:17 dustman-laptop kernel: [   29.640255] audit(1217634936.504:1): initialized
Aug  2 02:56:17 dustman-laptop kernel: [   29.640481] highmem bounce pool size: 64 pages
Aug  2 02:56:17 dustman-laptop kernel: [   29.642630] VFS: Disk quotas dquot_6.5.1
Aug  2 02:56:17 dustman-laptop kernel: [   29.642717] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug  2 02:56:17 dustman-laptop kernel: [   29.642894] io scheduler noop registered
Aug  2 02:56:17 dustman-laptop kernel: [   29.642897] io scheduler anticipatory registered
Aug  2 02:56:17 dustman-laptop kernel: [   29.642899] io scheduler deadline registered
Aug  2 02:56:17 dustman-laptop kernel: [   29.642913] io scheduler cfq registered (default)
Aug  2 02:56:17 dustman-laptop kernel: [   30.317452] isapnp: Scanning for PnP cards...
Aug  2 02:56:17 dustman-laptop kernel: [   30.673362] isapnp: No Plug & Play device found
Aug  2 02:56:17 dustman-laptop kernel: [   30.703641] Real Time Clock Driver v1.12ac
Aug  2 02:56:17 dustman-laptop kernel: [   30.703771] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug  2 02:56:17 dustman-laptop kernel: [   30.705075] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug  2 02:56:17 dustman-laptop kernel: [   30.705174] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug  2 02:56:17 dustman-laptop kernel: [   30.705282] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Aug  2 02:56:17 dustman-laptop kernel: [   30.707704] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug  2 02:56:17 dustman-laptop kernel: [   30.707710] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug  2 02:56:17 dustman-laptop kernel: [   30.713248] mice: PS/2 mouse device common for all mice
Aug  2 02:56:17 dustman-laptop kernel: [   30.713383] EISA: Probing bus 0 at eisa.0
Aug  2 02:56:17 dustman-laptop kernel: [   30.713393] Cannot allocate resource for EISA slot 1
Aug  2 02:56:17 dustman-laptop kernel: [   30.713425] Cannot allocate resource for EISA slot 8
Aug  2 02:56:17 dustman-laptop kernel: [   30.713427] EISA: Detected 0 cards.
Aug  2 02:56:17 dustman-laptop kernel: [   30.713431] cpuidle: using governor ladder
Aug  2 02:56:17 dustman-laptop kernel: [   30.713433] cpuidle: using governor menu
Aug  2 02:56:17 dustman-laptop kernel: [   30.713547] NET: Registered protocol family 1
Aug  2 02:56:17 dustman-laptop kernel: [   30.713579] Using IPI No-Shortcut mode
Aug  2 02:56:17 dustman-laptop kernel: [   30.713621] registered taskstats version 1
Aug  2 02:56:17 dustman-laptop kernel: [   30.714690]   Magic number: 4:418:958
Aug  2 02:56:17 dustman-laptop kernel: [   30.714769]   hash matches device ptyzf
Aug  2 02:56:17 dustman-laptop kernel: [   30.714840]   hash matches device oldmem
Aug  2 02:56:17 dustman-laptop kernel: [   30.714864] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug  2 02:56:17 dustman-laptop kernel: [   30.714866] EDD information not available.
Aug  2 02:56:17 dustman-laptop kernel: [   30.715250] Freeing unused kernel memory: 368k freed
Aug  2 02:56:17 dustman-laptop kernel: [   30.753114] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug  2 02:56:17 dustman-laptop kernel: [   31.947468] fuse init (API version 7.9)
Aug  2 02:56:17 dustman-laptop kernel: [   31.962426] ACPI: Transitioning device [FAN1] to D3
Aug  2 02:56:17 dustman-laptop kernel: [   31.962431] ACPI: Transitioning device [FAN1] to D3
Aug  2 02:56:17 dustman-laptop kernel: [   31.962434] ACPI: Fan [FAN1] (off)
Aug  2 02:56:17 dustman-laptop kernel: [   31.969466] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Aug  2 02:56:17 dustman-laptop kernel: [   31.969474] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug  2 02:56:17 dustman-laptop kernel: [   31.969491] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug  2 02:56:17 dustman-laptop kernel: [   32.177456] ACPI: Thermal Zone [TZCR] (58 C)
Aug  2 02:56:17 dustman-laptop kernel: [   32.881264] SCSI subsystem initialized
Aug  2 02:56:17 dustman-laptop kernel: [   32.966427] usbcore: registered new interface driver usbfs
Aug  2 02:56:17 dustman-laptop kernel: [   32.966457] usbcore: registered new interface driver hub
Aug  2 02:56:17 dustman-laptop kernel: [   32.981016] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug  2 02:56:17 dustman-laptop kernel: [   32.981023] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug  2 02:56:17 dustman-laptop kernel: [   33.001041] usbcore: registered new device driver usb
Aug  2 02:56:17 dustman-laptop kernel: [   33.013041] ATIIXP: IDE controller (0x1002:0x4376 rev 0x80) at  PCI slot 0000:00:14.1
Aug  2 02:56:17 dustman-laptop kernel: [   33.013275] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Aug  2 02:56:17 dustman-laptop kernel: [   33.013279] ACPI: PCI Interrupt 0000:00:14.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Aug  2 02:56:17 dustman-laptop kernel: [   33.013294] ATIIXP: not 100% native mode: will probe irqs later
Aug  2 02:56:17 dustman-laptop kernel: [   33.013305]     ide0: BM-DMA at 0x8460-0x8467, BIOS settings: hda:pio, hdb:pio
Aug  2 02:56:17 dustman-laptop kernel: [   33.013324]     ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdc:DMA, hdd:pio
Aug  2 02:56:17 dustman-laptop kernel: [   33.089678] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Aug  2 02:56:17 dustman-laptop kernel: [   34.653699] hdc: MATSHITADVD-RAM UJ-841S, ATAPI CD/DVD-ROM drive
Aug  2 02:56:17 dustman-laptop kernel: [   34.653915] hdc: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
Aug  2 02:56:17 dustman-laptop kernel: [   34.653922] hdc: set_drive_speed_status: error=0x04 { AbortedCommand }
Aug  2 02:56:17 dustman-laptop kernel: [   34.653936] hdc: UDMA/33 mode selected
Aug  2 02:56:17 dustman-laptop kernel: [   34.655071] ide1 at 0x170-0x177,0x376 on irq 15
Aug  2 02:56:17 dustman-laptop kernel: [   34.660953] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
Aug  2 02:56:17 dustman-laptop kernel: [   34.661137] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
Aug  2 02:56:17 dustman-laptop kernel: [   34.661141] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
Aug  2 02:56:17 dustman-laptop kernel: [   34.662234] scsi0 : sata_sil
Aug  2 02:56:17 dustman-laptop kernel: [   34.662466] scsi1 : sata_sil
Aug  2 02:56:17 dustman-laptop kernel: [   34.662753] ata1: SATA max UDMA/100 mmio m512@0xc0004000 tf 0xc0004080 irq 11
Aug  2 02:56:17 dustman-laptop kernel: [   34.662758] ata2: SATA max UDMA/100 mmio m512@0xc0004000 tf 0xc00040c0 irq 11
Aug  2 02:56:17 dustman-laptop kernel: [   35.129236] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug  2 02:56:17 dustman-laptop kernel: [   35.139081] ata1.00: ATA-7: FUJITSU MHV2060BH, 00000028, max UDMA/100
Aug  2 02:56:17 dustman-laptop kernel: [   35.139085] ata1.00: 117210240 sectors, multi 16: LBA48 NCQ (depth 0/32)
Aug  2 02:56:17 dustman-laptop kernel: [   35.155086] ata1.00: configured for UDMA/100
Aug  2 02:56:17 dustman-laptop kernel: [   35.469196] ata2: SATA link down (SStatus 0 SControl 300)
Aug  2 02:56:17 dustman-laptop kernel: [   35.469350] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2060B 0000 PQ: 0 ANSI: 5
Aug  2 02:56:17 dustman-laptop kernel: [   35.472155] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Aug  2 02:56:17 dustman-laptop kernel: [   35.472172] ohci_hcd 0000:00:13.0: OHCI Host Controller
Aug  2 02:56:17 dustman-laptop kernel: [   35.472658] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Aug  2 02:56:17 dustman-laptop kernel: [   35.472678] ohci_hcd 0000:00:13.0: irq 11, io mem 0xc0005000
Aug  2 02:56:17 dustman-laptop kernel: [   35.529346] usb usb1: configuration #1 chosen from 1 choice
Aug  2 02:56:17 dustman-laptop kernel: [   35.529378] hub 1-0:1.0: USB hub found
Aug  2 02:56:17 dustman-laptop kernel: [   35.529390] hub 1-0:1.0: 4 ports detected
Aug  2 02:56:17 dustman-laptop kernel: [   35.633293] ACPI: PCI Interrupt 0000:00:13.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Aug  2 02:56:17 dustman-laptop kernel: [   35.633314] ohci_hcd 0000:00:13.1: OHCI Host Controller
Aug  2 02:56:17 dustman-laptop kernel: [   35.633340] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Aug  2 02:56:17 dustman-laptop kernel: [   35.633356] ohci_hcd 0000:00:13.1: irq 11, io mem 0xc0006000
Aug  2 02:56:17 dustman-laptop kernel: [   35.693305] usb usb2: configuration #1 chosen from 1 choice
Aug  2 02:56:17 dustman-laptop kernel: [   35.693332] hub 2-0:1.0: USB hub found
Aug  2 02:56:17 dustman-laptop kernel: [   35.693342] hub 2-0:1.0: 4 ports detected
Aug  2 02:56:17 dustman-laptop kernel: [   35.797536] ACPI: PCI Interrupt 0000:00:13.2[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Aug  2 02:56:17 dustman-laptop kernel: [   35.797555] ehci_hcd 0000:00:13.2: EHCI Host Controller
Aug  2 02:56:17 dustman-laptop kernel: [   35.797580] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Aug  2 02:56:17 dustman-laptop kernel: [   35.797639] ehci_hcd 0000:00:13.2: irq 11, io mem 0xc0007000
Aug  2 02:56:17 dustman-laptop kernel: [   35.937162] usb 1-1: new low speed USB device using ohci_hcd and address 2
Aug  2 02:56:17 dustman-laptop kernel: [   35.949163] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug  2 02:56:17 dustman-laptop kernel: [   35.949305] usb usb3: configuration #1 chosen from 1 choice
Aug  2 02:56:17 dustman-laptop kernel: [   35.949334] hub 3-0:1.0: USB hub found
Aug  2 02:56:17 dustman-laptop kernel: [   35.949341] hub 3-0:1.0: 8 ports detected
Aug  2 02:56:17 dustman-laptop kernel: [   36.056536] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Aug  2 02:56:17 dustman-laptop kernel: [   36.106515] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[c0205800-c0205fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug  2 02:56:17 dustman-laptop kernel: [   36.107858] 8139too Fast Ethernet driver 0.9.28
Aug  2 02:56:17 dustman-laptop kernel: [   36.121115] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
Aug  2 02:56:17 dustman-laptop kernel: [   36.121127] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Aug  2 02:56:17 dustman-laptop kernel: [   36.122411] eth0: RealTek RTL8139 at 0xa000, 00:a0:d1:33:4b:7d, IRQ 10
Aug  2 02:56:17 dustman-laptop kernel: [   36.146710] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Aug  2 02:56:17 dustman-laptop kernel: [   36.146720] Uniform CD-ROM driver Revision: 3.20
Aug  2 02:56:17 dustman-laptop kernel: [   36.147399] Driver 'sd' needs updating - please use bus_type methods
Aug  2 02:56:17 dustman-laptop kernel: [   36.147501] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
Aug  2 02:56:17 dustman-laptop kernel: [   36.147516] sd 0:0:0:0: [sda] Write Protect is off
Aug  2 02:56:17 dustman-laptop kernel: [   36.147536] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  2 02:56:17 dustman-laptop kernel: [   36.147589] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
Aug  2 02:56:17 dustman-laptop kernel: [   36.147599] sd 0:0:0:0: [sda] Write Protect is off
Aug  2 02:56:17 dustman-laptop kernel: [   36.147618] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  2 02:56:17 dustman-laptop kernel: [   36.147622]  sda: sda1 sda2 sda3 sda4
Aug  2 02:56:17 dustman-laptop kernel: [   36.252303] sd 0:0:0:0: [sda] Attached SCSI disk
Aug  2 02:56:17 dustman-laptop kernel: [   36.259826] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug  2 02:56:17 dustman-laptop kernel: [   36.569183] Attempting manual resume
Aug  2 02:56:17 dustman-laptop kernel: [   36.598472] kjournald starting.  Commit interval 5 seconds
Aug  2 02:56:17 dustman-laptop kernel: [   36.598489] EXT3-fs: mounted filesystem with ordered data mode.
Aug  2 02:56:17 dustman-laptop kernel: [   36.721135] usb 3-2: new high speed USB device using ehci_hcd and address 3
Aug  2 02:56:17 dustman-laptop kernel: [   36.874977] usb 3-2: configuration #1 chosen from 1 choice
Aug  2 02:56:17 dustman-laptop kernel: [   37.177092] usb 1-1: new low speed USB device using ohci_hcd and address 3
Aug  2 02:56:17 dustman-laptop kernel: [   37.388171] usb 1-1: configuration #1 chosen from 1 choice
Aug  2 02:56:17 dustman-laptop kernel: [   49.810007] ACPI Error (evxfevnt-0383): Could not disable RealTimeClock events [20070126]
Aug  2 02:56:17 dustman-laptop kernel: [   51.510051] ACPI Error (evxfevnt-0383): Could not disable RealTimeClock events [20070126]
Aug  2 02:56:17 dustman-laptop kernel: [   52.590107] input: PC Speaker as /devices/platform/pcspkr/input/input2
Aug  2 02:56:17 dustman-laptop kernel: [   56.281126] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug  2 02:56:17 dustman-laptop kernel: [   56.290381] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug  2 02:56:17 dustman-laptop kernel: [   56.368058] Linux agpgart interface v0.102
Aug  2 02:56:17 dustman-laptop kernel: [   56.559409] input: Power Button (FF) as /devices/virtual/input/input3
Aug  2 02:56:17 dustman-laptop kernel: [   56.583546] ACPI: Power Button (FF) [PWRF]
Aug  2 02:56:17 dustman-laptop kernel: [   56.583623] input: Power Button (CM) as /devices/virtual/input/input4
Aug  2 02:56:17 dustman-laptop kernel: [   56.615532] ACPI: Power Button (CM) [PWRB]
Aug  2 02:56:17 dustman-laptop kernel: [   56.615609] input: Lid Switch as /devices/virtual/input/input5
Aug  2 02:56:17 dustman-laptop kernel: [   56.627638] ACPI: Lid Switch [LID]
Aug  2 02:56:17 dustman-laptop kernel: [   56.957003] ACPI: AC Adapter [ADP0] (on-line)
Aug  2 02:56:17 dustman-laptop kernel: [   56.990801] Yenta: CardBus bridge found at 0000:02:06.0 [1179:ff10]
Aug  2 02:56:17 dustman-laptop kernel: [   56.990839] Yenta: Using CSCINT to route CSC interrupts to PCI
Aug  2 02:56:17 dustman-laptop kernel: [   56.990842] Yenta: Routing CardBus interrupts to PCI
Aug  2 02:56:17 dustman-laptop kernel: [   56.990849] Yenta TI: socket 0000:02:06.0, mfunc 0x01111002, devctl 0x44
Aug  2 02:56:17 dustman-laptop kernel: [   57.136700] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
Aug  2 02:56:17 dustman-laptop kernel: [   57.136710] synaptics: Toshiba Satellite A100 detected, limiting rate to 40pps.
Aug  2 02:56:17 dustman-laptop kernel: [   57.169451] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
Aug  2 02:56:17 dustman-laptop kernel: [   57.179715] ACPI: Battery Slot [BAT0] (battery present)
Aug  2 02:56:17 dustman-laptop kernel: [   57.200382] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:16/LNXVIDEO:00/input/input7
Aug  2 02:56:17 dustman-laptop kernel: [   57.220162] Yenta: ISA IRQ mask 0x00f8, PCI irq 11
Aug  2 02:56:17 dustman-laptop kernel: [   57.220170] Socket status: 30000006
Aug  2 02:56:17 dustman-laptop kernel: [   57.220174] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
Aug  2 02:56:17 dustman-laptop kernel: [   57.220178] cs: IO port probe 0xa000-0xafff: clean.
Aug  2 02:56:17 dustman-laptop kernel: [   57.220483] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
Aug  2 02:56:17 dustman-laptop kernel: [   57.227840] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Aug  2 02:56:17 dustman-laptop kernel: [   57.231607] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Aug  2 02:56:17 dustman-laptop kernel: [   57.582516] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Aug  2 02:56:17 dustman-laptop kernel: [   57.615317] [fglrx] Maximum main memory to use for locked dma buffers: 1170 MBytes.
Aug  2 02:56:17 dustman-laptop kernel: [   57.615363] [fglrx] ASYNCIO init succeed!
Aug  2 02:56:17 dustman-laptop kernel: [   57.615851] [fglrx] PAT is enabled successfully!
Aug  2 02:56:17 dustman-laptop kernel: [   57.697728] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
Aug  2 02:56:17 dustman-laptop kernel: [   58.686070] usbcore: registered new interface driver libusual
Aug  2 02:56:17 dustman-laptop kernel: [   58.882949] usbcore: registered new interface driver hiddev
Aug  2 02:56:17 dustman-laptop kernel: [   58.900234] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.0/input/input8
Aug  2 02:56:17 dustman-laptop kernel: [   58.923781] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-1
Aug  2 02:56:17 dustman-laptop kernel: [   58.923803] usbcore: registered new interface driver usbhid
Aug  2 02:56:17 dustman-laptop kernel: [   58.923807] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug  2 02:56:17 dustman-laptop kernel: [   59.065127] cs: IO port probe 0x100-0x3af: clean.
Aug  2 02:56:17 dustman-laptop kernel: [   59.068005] cs: IO port probe 0x3e0-0x4ff: clean.
Aug  2 02:56:17 dustman-laptop kernel: [   59.069033] cs: IO port probe 0x820-0x8ff: clean.
Aug  2 02:56:17 dustman-laptop kernel: [   59.069890] cs: IO port probe 0xc00-0xcf7: clean.
Aug  2 02:56:17 dustman-laptop kernel: [   59.070791] cs: IO port probe 0xa00-0xaff: clean.
Aug  2 02:56:17 dustman-laptop kernel: [   59.228554] Initializing USB Mass Storage driver...
Aug  2 02:56:17 dustman-laptop kernel: [   59.239324] scsi2 : SCSI emulation for USB Mass Storage devices
Aug  2 02:56:17 dustman-laptop kernel: [   59.240332] usbcore: registered new interface driver usb-storage
Aug  2 02:56:17 dustman-laptop kernel: [   59.240339] USB Mass Storage support registered.
Aug  2 02:56:17 dustman-laptop kernel: [   59.986280] ACPI: PCI Interrupt 0000:00:14.2[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Aug  2 02:56:17 dustman-laptop kernel: [   61.011196] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
Aug  2 02:56:17 dustman-laptop kernel: [   61.014735] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
Aug  2 02:56:17 dustman-laptop kernel: [   61.809047] ACPI Error (evxfevnt-0383): Could not disable RealTimeClock events [20070126]
Aug  2 02:56:17 dustman-laptop kernel: [   62.054934] lp: driver loaded but no devices found
Aug  2 02:56:17 dustman-laptop kernel: [   62.317485] Adding 996020k swap on /dev/sda3.  Priority:-1 extents:1 across:996020k
Aug  2 02:56:17 dustman-laptop kernel: [   63.803456] EXT3 FS on sda4, internal journal
Aug  2 02:56:17 dustman-laptop kernel: [   64.291457] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-E30N  UE01 PQ: 0 ANSI: 0
Aug  2 02:56:17 dustman-laptop kernel: [   64.291855] scsi 2:0:0:0: Attached scsi generic sg1 type 5
Aug  2 02:56:17 dustman-laptop kernel: [   64.379694] Driver 'sr' needs updating - please use bus_type methods
Aug  2 02:56:17 dustman-laptop kernel: [   65.051427] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Aug  2 02:56:17 dustman-laptop kernel: [   65.763352] kjournald starting.  Commit interval 5 seconds
Aug  2 02:56:17 dustman-laptop kernel: [   65.779325] EXT3 FS on sda1, internal journal
Aug  2 02:56:17 dustman-laptop kernel: [   65.779331] EXT3-fs: mounted filesystem with ordered data mode.
Aug  2 02:56:17 dustman-laptop kernel: [   66.813592] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug  2 02:56:17 dustman-laptop kernel: [   67.949530] No dock devices found.
Aug  2 02:56:18 dustman-laptop kernel: [   71.330236] apm: BIOS not found.
Aug  2 02:56:19 dustman-laptop kernel: [   72.044585] ppdev: user-space parallel port driver
Aug  2 02:56:19 dustman-laptop kernel: [   72.579057] audit(1217634979.769:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5143 profile="/usr/sbin/cupsd" namespace="default"
Aug  2 02:56:21 dustman-laptop dhcdbd: Started up.
Aug  2 02:56:26 dustman-laptop kernel: [   78.968927] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Aug  2 02:56:26 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Aug  2 02:56:30 dustman-laptop kernel: [   83.429416] NET: Registered protocol family 17
Aug  2 02:56:31 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Aug  2 02:56:31 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Aug  2 02:56:31 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Aug  2 02:56:31 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Aug  2 02:56:31 dustman-laptop kernel: [   84.509488] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
Aug  2 02:56:31 dustman-laptop kernel: [   84.509496] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Aug  2 02:56:35 dustman-laptop kernel: [   88.200939] NET: Registered protocol family 10
Aug  2 02:56:35 dustman-laptop kernel: [   88.201172] lo: Disabled Privacy Extensions
Aug  2 02:56:35 dustman-laptop kernel: [   88.218408] [fglrx] GART Table is not in FRAME_BUFFER range
Aug  2 02:56:35 dustman-laptop kernel: [   88.218423] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Aug  2 02:56:35 dustman-laptop kernel: [   88.218426] [fglrx] Reserve Block - 1 offset =  0Xfff5000 length = 0Xb000
Aug  2 02:56:35 dustman-laptop kernel: [   88.576037] [fglrx] interrupt source 10000000 successfully enabled
Aug  2 02:56:35 dustman-laptop kernel: [   88.576047] [fglrx] enable ID = 0x00000004
Aug  2 02:56:35 dustman-laptop kernel: [   88.576403] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Aug  2 02:56:54 dustman-laptop kernel: [  106.974712] hda-intel: Invalid position buffer, using LPIB read method instead.
Aug  2 02:57:14 dustman-laptop pulseaudio[5766]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug  2 02:57:14 dustman-laptop pulseaudio[5766]: alsa-util.c: Unable to load mixer: No such file or directory
Aug  2 02:57:14 dustman-laptop pulseaudio[5766]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug  2 02:57:14 dustman-laptop pulseaudio[5766]: alsa-util.c: Unable to load mixer: No such file or directory
Aug  2 02:59:27 dustman-laptop kernel: [  260.788979] [fglrx] interrupt source 10000000 successfully disabled!
Aug  2 02:59:27 dustman-laptop kernel: [  260.788987] [fglrx] enable ID = 0x00000000
Aug  2 02:59:27 dustman-laptop kernel: [  260.788990] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000004
Aug  2 02:59:29 dustman-laptop kernel: [  262.399401] ACPI Error (evxfevnt-0383): Could not disable RealTimeClock events [20070126]
Aug  2 02:59:29 dustman-laptop kernel: [  262.724438] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug  2 02:59:30 dustman-laptop exiting on signal 15
Aug  2 11:56:53 dustman-laptop syslogd 1.5.0#1ubuntu1: restart.
Aug  2 11:56:53 dustman-laptop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug  2 11:56:53 dustman-laptop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug  2 11:56:53 dustman-laptop kernel: Symbols match kernel version 2.6.24.
Aug  2 11:56:53 dustman-laptop kernel: Loaded 24027 symbols from 91 modules.
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000004fea0000 (usable)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]  BIOS-e820: 000000004fea0000 - 000000004feb0000 (ACPI data)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]  BIOS-e820: 000000004feb0000 - 000000004ff00000 (ACPI NVS)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]  BIOS-e820: 000000004ff00000 - 0000000050000000 (reserved)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] 382MB HIGHMEM available.
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] 896MB LOWMEM available.
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] found SMP MP-table at 000f7630
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Zone PFN ranges:
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]   DMA             0 ->     4096
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]   HighMem    229376 ->   327328
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Movable zone start PFN for each node
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000]     0:        0 ->   327328
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] DMI present.
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F75E0 checksum 0
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: RSDP 000F75E0, 0014 (r0 TOSINV)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: RSDT 4FEAAAE6, 0038 (r1 TOSINV   RSDT    6040000  LTP        0)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: FACP 4FEAFEF6, 0074 (r1 TOSINV Goldfish  6040000 ATI     F4240)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: DSDT 4FEAAF3A, 4FBC (r1 TOSINV    SB450  6040000 MSFT  100000E)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: FACS 4FEB0FC0, 0040
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: APIC 4FEAFF6A, 005A (r1 TOSINV ^I APIC    6040000  LTP        0)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: MCFG 4FEAFFC4, 003C (r1 TOSINV   MCFG    6040000  LTP        0)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: SSDT 4FEAAD19, 0221 (r1 TOSINV  Cpu0Cst     3001 INTL 20030224)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: SSDT 4FEAAB1E, 01FB (r1 TOSINV    CpuPm     3000 INTL 20030224)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: DMI detected: Toshiba
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x8008
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Processor #0 6:13 APIC version 20
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:90000000)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324771
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Kernel command line: root=UUID=3a20c981-7908-4a4a-b830-011f73b58c49 ro irqpoll quiet splash
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Misrouted IRQ fixup and polling support enabled
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] This may significantly impact system performance
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Initializing CPU#0
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug  2 11:56:53 dustman-laptop kernel: [    0.000000] Detected 1592.442 MHz processor.
Aug  2 11:56:53 dustman-laptop kernel: [   29.942393] Console: colour VGA+ 80x25
Aug  2 11:56:53 dustman-laptop kernel: [   29.942398] console [tty0] enabled
Aug  2 11:56:53 dustman-laptop kernel: [   29.943393] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug  2 11:56:53 dustman-laptop kernel: [   29.944236] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug  2 11:56:53 dustman-laptop kernel: [   30.005786] Memory: 1285564k/1309312k available (2177k kernel code, 22492k reserved, 1006k data, 368k init, 391808k highmem)
Aug  2 11:56:53 dustman-laptop kernel: [   30.005798] virtual kernel memory layout:
Aug  2 11:56:53 dustman-laptop kernel: [   30.005799]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug  2 11:56:53 dustman-laptop kernel: [   30.005800]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug  2 11:56:53 dustman-laptop kernel: [   30.005802]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug  2 11:56:53 dustman-laptop kernel: [   30.005803]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug  2 11:56:53 dustman-laptop kernel: [   30.005804]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug  2 11:56:53 dustman-laptop kernel: [   30.005806]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug  2 11:56:53 dustman-laptop kernel: [   30.005807]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug  2 11:56:53 dustman-laptop kernel: [   30.005811] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug  2 11:56:53 dustman-laptop kernel: [   30.005896] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Aug  2 11:56:53 dustman-laptop kernel: [   30.085953] Calibrating delay using timer specific routine.. 3197.86 BogoMIPS (lpj=6395727)
Aug  2 11:56:53 dustman-laptop kernel: [   30.086007] Security Framework initialized
Aug  2 11:56:53 dustman-laptop kernel: [   30.086024] SELinux:  Disabled at boot.
Aug  2 11:56:53 dustman-laptop kernel: [   30.086050] AppArmor: AppArmor initialized
Aug  2 11:56:53 dustman-laptop kernel: [   30.086056] Failure registering capabilities with primary security module.
Aug  2 11:56:53 dustman-laptop kernel: [   30.086067] Mount-cache hash table entries: 512
Aug  2 11:56:53 dustman-laptop kernel: [   30.086280] Initializing cgroup subsys ns
Aug  2 11:56:53 dustman-laptop kernel: [   30.086290] Initializing cgroup subsys cpuacct
Aug  2 11:56:53 dustman-laptop kernel: [   30.086323] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug  2 11:56:53 dustman-laptop kernel: [   30.086325] CPU: L2 cache: 1024K
Aug  2 11:56:53 dustman-laptop kernel: [   30.086343] Compat vDSO mapped to ffffe000.
Aug  2 11:56:53 dustman-laptop kernel: [   30.086364] Checking 'hlt' instruction... OK.
Aug  2 11:56:53 dustman-laptop kernel: [   30.102426] SMP alternatives: switching to UP code
Aug  2 11:56:53 dustman-laptop kernel: [   30.104579] Freeing SMP alternatives: 11k freed
Aug  2 11:56:53 dustman-laptop kernel: [   30.104724] Early unpacking initramfs... done
Aug  2 11:56:53 dustman-laptop kernel: [   30.492665] ACPI: Core revision 20070126
Aug  2 11:56:53 dustman-laptop kernel: [   30.492745] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug  2 11:56:53 dustman-laptop kernel: [   30.511107] CPU0: Intel(R) Celeron(R) M processor         1.60GHz stepping 08
Aug  2 11:56:53 dustman-laptop kernel: [   30.511137] Total of 1 processors activated (3197.86 BogoMIPS).
Aug  2 11:56:53 dustman-laptop kernel: [   30.511327] ENABLING IO-APIC IRQs
Aug  2 11:56:53 dustman-laptop kernel: [   30.511520] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug  2 11:56:53 dustman-laptop kernel: [   30.551425] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
Aug  2 11:56:53 dustman-laptop kernel: [   30.551428] ...trying to set up timer as Virtual Wire IRQ... works.
Aug  2 11:56:53 dustman-laptop kernel: [   30.697985] Brought up 1 CPUs
Aug  2 11:56:53 dustman-laptop kernel: [   30.698204] net_namespace: 64 bytes
Aug  2 11:56:53 dustman-laptop kernel: [   30.698213] Booting paravirtualized kernel on bare hardware
Aug  2 11:56:53 dustman-laptop kernel: [   30.698725] Time:  8:56:22  Date: 08/02/08
Aug  2 11:56:53 dustman-laptop kernel: [   30.698756] NET: Registered protocol family 16
Aug  2 11:56:53 dustman-laptop kernel: [   30.698965] EISA bus registered
Aug  2 11:56:53 dustman-laptop kernel: [   30.699011] ACPI: bus type pci registered
Aug  2 11:56:53 dustman-laptop kernel: [   30.699287] PCI: PCI BIOS revision 2.10 entry at 0xfd82c, last bus=4
Aug  2 11:56:53 dustman-laptop kernel: [   30.699289] PCI: Using configuration type 1
Aug  2 11:56:53 dustman-laptop kernel: [   30.699299] Setting up standard PCI resources
Aug  2 11:56:53 dustman-laptop kernel: [   30.715756] ACPI: Interpreter enabled
Aug  2 11:56:53 dustman-laptop kernel: [   30.715760] ACPI: (supports S0 S3 S4 S5)
Aug  2 11:56:53 dustman-laptop kernel: [   30.715775] ACPI: Using IOAPIC for interrupt routing
Aug  2 11:56:53 dustman-laptop kernel: [   30.716537] ACPI: EC: non-query interrupt received, switching to interrupt mode
Aug  2 11:56:53 dustman-laptop kernel: [   30.781660] ACPI: EC: GPE = 0x7, I/O: command/status = 0x66, data = 0x62
Aug  2 11:56:53 dustman-laptop kernel: [   30.781663] ACPI: EC: driver started in interrupt mode
Aug  2 11:56:53 dustman-laptop kernel: [   30.781704] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug  2 11:56:53 dustman-laptop kernel: [   30.783564] PCI: Transparent bridge - 0000:00:14.4
Aug  2 11:56:53 dustman-laptop kernel: [   30.785811] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
Aug  2 11:56:53 dustman-laptop kernel: [   30.785923] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
Aug  2 11:56:53 dustman-laptop kernel: [   30.786040] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
Aug  2 11:56:53 dustman-laptop kernel: [   30.786150] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
Aug  2 11:56:53 dustman-laptop kernel: [   30.786258] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
Aug  2 11:56:53 dustman-laptop kernel: [   30.786367] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
Aug  2 11:56:53 dustman-laptop kernel: [   30.786475] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
Aug  2 11:56:53 dustman-laptop kernel: [   30.786584] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
Aug  2 11:56:53 dustman-laptop kernel: [   30.786708] ACPI: Power Resource [PFA1] (off)
Aug  2 11:56:53 dustman-laptop kernel: [   30.786756] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug  2 11:56:53 dustman-laptop kernel: [   30.786791] pnp: PnP ACPI init
Aug  2 11:56:53 dustman-laptop kernel: [   30.786799] ACPI: bus type pnp registered
Aug  2 11:56:53 dustman-laptop kernel: [   30.804039] pnp: PnP ACPI: found 10 devices
Aug  2 11:56:53 dustman-laptop kernel: [   30.804042] ACPI: ACPI bus type pnp unregistered
Aug  2 11:56:53 dustman-laptop kernel: [   30.804046] PnPBIOS: Disabled by ACPI PNP
Aug  2 11:56:53 dustman-laptop kernel: [   30.804279] PCI: Using ACPI for IRQ routing
Aug  2 11:56:53 dustman-laptop kernel: [   30.804282] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug  2 11:56:53 dustman-laptop kernel: [   30.829940] NET: Registered protocol family 8
Aug  2 11:56:53 dustman-laptop kernel: [   30.829942] NET: Registered protocol family 20
Aug  2 11:56:53 dustman-laptop kernel: [   30.830017] AppArmor: AppArmor Filesystem Enabled
Aug  2 11:56:53 dustman-laptop kernel: [   30.833930] Time: tsc clocksource has been installed.
Aug  2 11:56:53 dustman-laptop kernel: [   30.841971] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.841980] system 00:08: ioport range 0x1080-0x1080 has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.841983] system 00:08: ioport range 0x220-0x22f has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.841987] system 00:08: ioport range 0x400-0x401 has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.841990] system 00:08: ioport range 0x40b-0x40b has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.841993] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.841996] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.841999] system 00:08: ioport range 0x530-0x537 has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842002] system 00:08: ioport range 0xc00-0xc01 has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842005] system 00:08: ioport range 0xc14-0xc14 has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842008] system 00:08: ioport range 0xc50-0xc52 has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842011] system 00:08: ioport range 0xc6c-0xc6c has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842014] system 00:08: ioport range 0xc6f-0xc6f has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842017] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842020] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842023] system 00:08: ioport range 0xcd8-0xcdf has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842026] system 00:08: ioport range 0x8000-0x805f has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842029] system 00:08: ioport range 0xf40-0xf47 has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842032] system 00:08: ioport range 0x280-0x293 has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842035] system 00:08: ioport range 0x87f-0x87f has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842041] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842044] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842047] system 00:09: iomem range 0x0-0xfff could not be reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.842051] system 00:09: iomem range 0xc0004800-0xc0004fff has been reserved
Aug  2 11:56:53 dustman-laptop kernel: [   30.872493] PCI: Bridge: 0000:00:01.0
Aug  2 11:56:53 dustman-laptop kernel: [   30.872496]   IO window: 9000-9fff
Aug  2 11:56:53 dustman-laptop kernel: [   30.872500]   MEM window: c0100000-c01fffff
Aug  2 11:56:53 dustman-laptop kernel: [   30.872504]   PREFETCH window: d0000000-dfffffff
Aug  2 11:56:53 dustman-laptop kernel: [   30.872511] PCI: Bus 3, cardbus bridge: 0000:02:06.0
Aug  2 11:56:53 dustman-laptop kernel: [   30.872513]   IO window: 0000a400-0000a4ff
Aug  2 11:56:53 dustman-laptop kernel: [   30.872520]   IO window: 0000a800-0000a8ff
Aug  2 11:56:53 dustman-laptop kernel: [   30.872527]   PREFETCH window: 64000000-67ffffff
Aug  2 11:56:53 dustman-laptop kernel: [   30.872534]   MEM window: 68000000-6bffffff
Aug  2 11:56:53 dustman-laptop kernel: [   30.872540] PCI: Bridge: 0000:00:14.4
Aug  2 11:56:53 dustman-laptop kernel: [   30.872544]   IO window: a000-afff
Aug  2 11:56:53 dustman-laptop kernel: [   30.872551]   MEM window: c0200000-c02fffff
Aug  2 11:56:53 dustman-laptop kernel: [   30.872557]   PREFETCH window: disabled.
Aug  2 11:56:53 dustman-laptop kernel: [   30.872601] PCI: Enabling device 0000:02:06.0 (0004 -> 0007)
Aug  2 11:56:53 dustman-laptop kernel: [   30.872610] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 23 (level, low) -> IRQ 16
Aug  2 11:56:53 dustman-laptop kernel: [   30.872628] NET: Registered protocol family 2
Aug  2 11:56:53 dustman-laptop kernel: [   30.910008] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug  2 11:56:53 dustman-laptop kernel: [   30.910308] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug  2 11:56:53 dustman-laptop kernel: [   30.912354] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug  2 11:56:53 dustman-laptop kernel: [   30.913618] TCP: Hash tables configured (established 131072 bind 65536)
Aug  2 11:56:53 dustman-laptop kernel: [   30.913624] TCP reno registered
Aug  2 11:56:53 dustman-laptop kernel: [   30.922165] checking if image is initramfs... it is
Aug  2 11:56:53 dustman-laptop kernel: [   31.727514] Freeing initrd memory: 7305k freed
Aug  2 11:56:53 dustman-laptop kernel: [   31.728335] audit: initializing netlink socket (disabled)
Aug  2 11:56:53 dustman-laptop kernel: [   31.728358] audit(1217667382.552:1): initialized
Aug  2 11:56:53 dustman-laptop kernel: [   31.728585] highmem bounce pool size: 64 pages
Aug  2 11:56:53 dustman-laptop kernel: [   31.730731] VFS: Disk quotas dquot_6.5.1
Aug  2 11:56:53 dustman-laptop kernel: [   31.730817] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug  2 11:56:53 dustman-laptop kernel: [   31.730994] io scheduler noop registered
Aug  2 11:56:53 dustman-laptop kernel: [   31.730997] io scheduler anticipatory registered
Aug  2 11:56:53 dustman-laptop kernel: [   31.730999] io scheduler deadline registered
Aug  2 11:56:53 dustman-laptop kernel: [   31.731014] io scheduler cfq registered (default)
Aug  2 11:56:53 dustman-laptop kernel: [   32.406069] isapnp: Scanning for PnP cards...
Aug  2 11:56:53 dustman-laptop kernel: [   32.761980] isapnp: No Plug & Play device found
Aug  2 11:56:53 dustman-laptop kernel: [   32.792217] Real Time Clock Driver v1.12ac
Aug  2 11:56:53 dustman-laptop kernel: [   32.792353] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug  2 11:56:53 dustman-laptop kernel: [   32.794072] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug  2 11:56:53 dustman-laptop kernel: [   32.794166] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug  2 11:56:53 dustman-laptop kernel: [   32.794276] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
Aug  2 11:56:53 dustman-laptop kernel: [   32.796562] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug  2 11:56:53 dustman-laptop kernel: [   32.796567] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug  2 11:56:53 dustman-laptop kernel: [   32.809765] mice: PS/2 mouse device common for all mice
Aug  2 11:56:53 dustman-laptop kernel: [   32.809897] EISA: Probing bus 0 at eisa.0
Aug  2 11:56:53 dustman-laptop kernel: [   32.809907] Cannot allocate resource for EISA slot 1
Aug  2 11:56:53 dustman-laptop kernel: [   32.809939] Cannot allocate resource for EISA slot 8
Aug  2 11:56:53 dustman-laptop kernel: [   32.809941] EISA: Detected 0 cards.
Aug  2 11:56:53 dustman-laptop kernel: [   32.809946] cpuidle: using governor ladder
Aug  2 11:56:53 dustman-laptop kernel: [   32.809948] cpuidle: using governor menu
Aug  2 11:56:53 dustman-laptop kernel: [   32.810062] NET: Registered protocol family 1
Aug  2 11:56:53 dustman-laptop kernel: [   32.810094] Using IPI No-Shortcut mode
Aug  2 11:56:53 dustman-laptop kernel: [   32.810137] registered taskstats version 1
Aug  2 11:56:53 dustman-laptop kernel: [   32.811205]   Magic number: 4:897:926
Aug  2 11:56:53 dustman-laptop kernel: [   32.811301]   hash matches device ptyxb
Aug  2 11:56:53 dustman-laptop kernel: [   32.811386] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug  2 11:56:53 dustman-laptop kernel: [   32.811388] EDD information not available.
Aug  2 11:56:53 dustman-laptop kernel: [   32.811771] Freeing unused kernel memory: 368k freed
Aug  2 11:56:53 dustman-laptop kernel: [   32.849713] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug  2 11:56:53 dustman-laptop kernel: [   34.043593] fuse init (API version 7.9)
Aug  2 11:56:53 dustman-laptop kernel: [   34.058527] ACPI: Transitioning device [FAN1] to D3
Aug  2 11:56:53 dustman-laptop kernel: [   34.058530] ACPI: Transitioning device [FAN1] to D3
Aug  2 11:56:53 dustman-laptop kernel: [   34.058534] ACPI: Fan [FAN1] (off)
Aug  2 11:56:53 dustman-laptop kernel: [   34.065543] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Aug  2 11:56:53 dustman-laptop kernel: [   34.065561] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug  2 11:56:53 dustman-laptop kernel: [   34.065579] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug  2 11:56:53 dustman-laptop kernel: [   34.273969] ACPI: Thermal Zone [TZCR] (36 C)
Aug  2 11:56:53 dustman-laptop kernel: [   34.970330] SCSI subsystem initialized
Aug  2 11:56:53 dustman-laptop kernel: [   35.061360] usbcore: registered new interface driver usbfs
Aug  2 11:56:53 dustman-laptop kernel: [   35.061392] usbcore: registered new interface driver hub
Aug  2 11:56:53 dustman-laptop kernel: [   35.073477] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Aug  2 11:56:53 dustman-laptop kernel: [   35.073484] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Aug  2 11:56:53 dustman-laptop kernel: [   35.093499] usbcore: registered new device driver usb
Aug  2 11:56:53 dustman-laptop kernel: [   35.105547] ATIIXP: IDE controller (0x1002:0x4376 rev 0x80) at  PCI slot 0000:00:14.1
Aug  2 11:56:53 dustman-laptop kernel: [   35.105577] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
Aug  2 11:56:53 dustman-laptop kernel: [   35.105590] ATIIXP: not 100% native mode: will probe irqs later
Aug  2 11:56:53 dustman-laptop kernel: [   35.105602]     ide0: BM-DMA at 0x8460-0x8467, BIOS settings: hda:pio, hdb:pio
Aug  2 11:56:53 dustman-laptop kernel: [   35.105620]     ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdc:DMA, hdd:pio
Aug  2 11:56:53 dustman-laptop kernel: [   35.170937] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Aug  2 11:56:53 dustman-laptop kernel: [   36.745870] hdc: MATSHITADVD-RAM UJ-841S, ATAPI CD/DVD-ROM drive
Aug  2 11:56:53 dustman-laptop kernel: [   36.746087] hdc: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
Aug  2 11:56:53 dustman-laptop kernel: [   36.746094] hdc: set_drive_speed_status: error=0x04 { AbortedCommand }
Aug  2 11:56:53 dustman-laptop kernel: [   36.746108] hdc: UDMA/33 mode selected
Aug  2 11:56:53 dustman-laptop kernel: [   36.747262] ide1 at 0x170-0x177,0x376 on irq 15
Aug  2 11:56:53 dustman-laptop kernel: [   36.752785] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
Aug  2 11:56:53 dustman-laptop kernel: [   36.752796] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
Aug  2 11:56:53 dustman-laptop kernel: [   36.753920] scsi0 : sata_sil
Aug  2 11:56:53 dustman-laptop kernel: [   36.754149] scsi1 : sata_sil
Aug  2 11:56:53 dustman-laptop kernel: [   36.754453] ata1: SATA max UDMA/100 mmio m512@0xc0004000 tf 0xc0004080 irq 18
Aug  2 11:56:53 dustman-laptop kernel: [   36.754458] ata2: SATA max UDMA/100 mmio m512@0xc0004000 tf 0xc00040c0 irq 18
Aug  2 11:56:53 dustman-laptop kernel: [   37.221376] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug  2 11:56:53 dustman-laptop kernel: [   37.231431] ata1.00: ATA-7: FUJITSU MHV2060BH, 00000028, max UDMA/100
Aug  2 11:56:53 dustman-laptop kernel: [   37.231435] ata1.00: 117210240 sectors, multi 16: LBA48 NCQ (depth 0/32)
Aug  2 11:56:53 dustman-laptop kernel: [   37.247431] ata1.00: configured for UDMA/100
Aug  2 11:56:53 dustman-laptop kernel: [   37.557634] ata2: SATA link down (SStatus 0 SControl 300)
Aug  2 11:56:53 dustman-laptop kernel: [   37.557789] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2060B 0000 PQ: 0 ANSI: 5
Aug  2 11:56:53 dustman-laptop kernel: [   37.560614] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19
Aug  2 11:56:53 dustman-laptop kernel: [   37.560630] ohci_hcd 0000:00:13.0: OHCI Host Controller
Aug  2 11:56:53 dustman-laptop kernel: [   37.561112] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Aug  2 11:56:53 dustman-laptop kernel: [   37.561137] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0005000
Aug  2 11:56:53 dustman-laptop kernel: [   37.621670] usb usb1: configuration #1 chosen from 1 choice
Aug  2 11:56:53 dustman-laptop kernel: [   37.621698] hub 1-0:1.0: USB hub found
Aug  2 11:56:53 dustman-laptop kernel: [   37.621710] hub 1-0:1.0: 4 ports detected
Aug  2 11:56:53 dustman-laptop kernel: [   37.725637] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19
Aug  2 11:56:53 dustman-laptop kernel: [   37.725658] ohci_hcd 0000:00:13.1: OHCI Host Controller
Aug  2 11:56:53 dustman-laptop kernel: [   37.725683] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Aug  2 11:56:53 dustman-laptop kernel: [   37.725701] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0006000
Aug  2 11:56:53 dustman-laptop kernel: [   37.785427] usb usb2: configuration #1 chosen from 1 choice
Aug  2 11:56:53 dustman-laptop kernel: [   37.785454] hub 2-0:1.0: USB hub found
Aug  2 11:56:53 dustman-laptop kernel: [   37.785466] hub 2-0:1.0: 4 ports detected
Aug  2 11:56:53 dustman-laptop kernel: [   37.889892] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
Aug  2 11:56:53 dustman-laptop kernel: [   37.889910] ehci_hcd 0000:00:13.2: EHCI Host Controller
Aug  2 11:56:53 dustman-laptop kernel: [   37.889937] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Aug  2 11:56:53 dustman-laptop kernel: [   37.889993] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0007000
Aug  2 11:56:53 dustman-laptop kernel: [   38.029482] usb 1-1: new low speed USB device using ohci_hcd and address 2
Aug  2 11:56:53 dustman-laptop kernel: [   38.041479] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug  2 11:56:53 dustman-laptop kernel: [   38.041615] usb usb3: configuration #1 chosen from 1 choice
Aug  2 11:56:53 dustman-laptop kernel: [   38.041643] hub 3-0:1.0: USB hub found
Aug  2 11:56:53 dustman-laptop kernel: [   38.041650] hub 3-0:1.0: 8 ports detected
Aug  2 11:56:53 dustman-laptop kernel: [   38.148766] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 18
Aug  2 11:56:53 dustman-laptop kernel: [   38.198754] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[c0205800-c0205fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Aug  2 11:56:53 dustman-laptop kernel: [   38.200888] 8139too Fast Ethernet driver 0.9.28
Aug  2 11:56:53 dustman-laptop kernel: [   38.213226] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 20 (level, low) -> IRQ 20
Aug  2 11:56:53 dustman-laptop kernel: [   38.214509] eth0: RealTek RTL8139 at 0xa000, 00:a0:d1:33:4b:7d, IRQ 20
Aug  2 11:56:53 dustman-laptop kernel: [   38.240405] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Aug  2 11:56:53 dustman-laptop kernel: [   38.240414] Uniform CD-ROM driver Revision: 3.20
Aug  2 11:56:53 dustman-laptop kernel: [   38.240549] Driver 'sd' needs updating - please use bus_type methods
Aug  2 11:56:53 dustman-laptop kernel: [   38.240646] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
Aug  2 11:56:53 dustman-laptop kernel: [   38.240661] sd 0:0:0:0: [sda] Write Protect is off
Aug  2 11:56:53 dustman-laptop kernel: [   38.240680] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  2 11:56:53 dustman-laptop kernel: [   38.240789] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
Aug  2 11:56:53 dustman-laptop kernel: [   38.240800] sd 0:0:0:0: [sda] Write Protect is off
Aug  2 11:56:53 dustman-laptop kernel: [   38.240818] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  2 11:56:53 dustman-laptop kernel: [   38.240822]  sda: sda1 sda2 sda3 sda4
Aug  2 11:56:53 dustman-laptop kernel: [   38.341393] sd 0:0:0:0: [sda] Attached SCSI disk
Aug  2 11:56:53 dustman-laptop kernel: [   38.348895] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug  2 11:56:53 dustman-laptop kernel: [   38.668029] Attempting manual resume
Aug  2 11:56:53 dustman-laptop kernel: [   38.698725] kjournald starting.  Commit interval 5 seconds
Aug  2 11:56:53 dustman-laptop kernel: [   38.698741] EXT3-fs: mounted filesystem with ordered data mode.
Aug  2 11:56:53 dustman-laptop kernel: [   38.814018] usb 3-2: new high speed USB device using ehci_hcd and address 3
Aug  2 11:56:53 dustman-laptop kernel: [   38.968216] usb 3-2: configuration #1 chosen from 1 choice
Aug  2 11:56:53 dustman-laptop kernel: [   39.273342] usb 1-1: new low speed USB device using ohci_hcd and address 3
Aug  2 11:56:53 dustman-laptop kernel: [   39.483497] usb 1-1: configuration #1 chosen from 1 choice
Aug  2 11:56:53 dustman-laptop kernel: [   50.316124] ACPI Error (evxfevnt-0383): Could not disable RealTimeClock events [20070126]
Aug  2 11:56:53 dustman-laptop kernel: [   51.827557] Linux agpgart interface v0.102
Aug  2 11:56:53 dustman-laptop kernel: [   51.931563] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug  2 11:56:53 dustman-laptop kernel: [   52.004349] input: PC Speaker as /devices/platform/pcspkr/input/input2
Aug  2 11:56:53 dustman-laptop kernel: [   52.171581] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug  2 11:56:53 dustman-laptop kernel: [   52.247550] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Aug  2 11:56:53 dustman-laptop kernel: [   52.685786] input: Power Button (FF) as /devices/virtual/input/input3
Aug  2 11:56:53 dustman-laptop kernel: [   52.699790] ACPI: Power Button (FF) [PWRF]
Aug  2 11:56:53 dustman-laptop kernel: [   52.699934] input: Power Button (CM) as /devices/virtual/input/input4
Aug  2 11:56:53 dustman-laptop kernel: [   52.715404] ACPI: Power Button (CM) [PWRB]
Aug  2 11:56:53 dustman-laptop kernel: [   52.715503] input: Lid Switch as /devices/virtual/input/input5
Aug  2 11:56:53 dustman-laptop kernel: [   52.715594] ACPI: Lid Switch [LID]
Aug  2 11:56:53 dustman-laptop kernel: [   52.811552] ACPI: AC Adapter [ADP0] (on-line)
Aug  2 11:56:53 dustman-laptop kernel: [   53.143571] Yenta: CardBus bridge found at 0000:02:06.0 [1179:ff10]
Aug  2 11:56:53 dustman-laptop kernel: [   53.143611] Yenta: Using CSCINT to route CSC interrupts to PCI
Aug  2 11:56:53 dustman-laptop kernel: [   53.143613] Yenta: Routing CardBus interrupts to PCI
Aug  2 11:56:53 dustman-laptop kernel: [   53.143620] Yenta TI: socket 0000:02:06.0, mfunc 0x01111002, devctl 0x44
Aug  2 11:56:53 dustman-laptop kernel: [   53.163554] ACPI: Battery Slot [BAT0] (battery present)
Aug  2 11:56:53 dustman-laptop kernel: [   53.376289] Yenta: ISA IRQ mask 0x0ef8, PCI irq 16
Aug  2 11:56:53 dustman-laptop kernel: [   53.376297] Socket status: 30000006
Aug  2 11:56:53 dustman-laptop kernel: [   53.376301] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
Aug  2 11:56:53 dustman-laptop kernel: [   53.376304] cs: IO port probe 0xa000-0xafff: clean.
Aug  2 11:56:53 dustman-laptop kernel: [   53.376608] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
Aug  2 11:56:53 dustman-laptop kernel: [   53.933963] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Aug  2 11:56:53 dustman-laptop kernel: [   54.028236] [fglrx] Maximum main memory to use for locked dma buffers: 1170 MBytes.
Aug  2 11:56:53 dustman-laptop kernel: [   54.028284] [fglrx] ASYNCIO init succeed!
Aug  2 11:56:53 dustman-laptop kernel: [   54.028539] [fglrx] PAT is enabled successfully!
Aug  2 11:56:53 dustman-laptop kernel: [   54.043890] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
Aug  2 11:56:53 dustman-laptop kernel: [   54.315825] ACPI Error (evxfevnt-0383): Could not disable RealTimeClock events [20070126]
Aug  2 11:56:53 dustman-laptop kernel: [   54.347040] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
Aug  2 11:56:53 dustman-laptop kernel: [   54.370790] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
Aug  2 11:56:53 dustman-laptop kernel: [   54.449212] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
Aug  2 11:56:53 dustman-laptop kernel: [   54.449222] synaptics: Toshiba Satellite A100 detected, limiting rate to 40pps.
Aug  2 11:56:53 dustman-laptop kernel: [   54.482415] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
Aug  2 11:56:53 dustman-laptop kernel: [   55.617644] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:16/LNXVIDEO:00/input/input7
Aug  2 11:56:53 dustman-laptop kernel: [   55.643273] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Aug  2 11:56:53 dustman-laptop kernel: [   55.864594] usbcore: registered new interface driver libusual
Aug  2 11:56:53 dustman-laptop kernel: [   55.886183] usbcore: registered new interface driver hiddev
Aug  2 11:56:53 dustman-laptop kernel: [   55.890287] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb1/1-1/1-1:1.0/input/input8
Aug  2 11:56:53 dustman-laptop kernel: [   55.907626] Initializing USB Mass Storage driver...
Aug  2 11:56:53 dustman-laptop kernel: [   55.910784] scsi2 : SCSI emulation for USB Mass Storage devices
Aug  2 11:56:53 dustman-laptop kernel: [   55.919142] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-1
Aug  2 11:56:53 dustman-laptop kernel: [   55.919167] usbcore: registered new interface driver usbhid
Aug  2 11:56:53 dustman-laptop kernel: [   55.919171] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug  2 11:56:53 dustman-laptop kernel: [   55.919313] usbcore: registered new interface driver usb-storage
Aug  2 11:56:53 dustman-laptop kernel: [   55.919316] USB Mass Storage support registered.
Aug  2 11:56:53 dustman-laptop kernel: [   57.327788] cs: IO port probe 0x100-0x3af: clean.
Aug  2 11:56:53 dustman-laptop kernel: [   57.330218] cs: IO port probe 0x3e0-0x4ff: clean.
Aug  2 11:56:53 dustman-laptop kernel: [   57.331260] cs: IO port probe 0x820-0x8ff: clean.
Aug  2 11:56:53 dustman-laptop kernel: [   57.332117] cs: IO port probe 0xc00-0xcf7: clean.
Aug  2 11:56:53 dustman-laptop kernel: [   57.333019] cs: IO port probe 0xa00-0xaff: clean.
Aug  2 11:56:53 dustman-laptop kernel: [   58.329188] ACPI Error (evxfevnt-0383): Could not disable RealTimeClock events [20070126]
Aug  2 11:56:53 dustman-laptop kernel: [   58.439116] lp: driver loaded but no devices found
Aug  2 11:56:53 dustman-laptop kernel: [   58.677946] Adding 996020k swap on /dev/sda3.  Priority:-1 extents:1 across:996020k
Aug  2 11:56:53 dustman-laptop kernel: [   59.239131] EXT3 FS on sda4, internal journal
Aug  2 11:56:53 dustman-laptop kernel: [   60.030857] kjournald starting.  Commit interval 5 seconds
Aug  2 11:56:53 dustman-laptop kernel: [   60.032223] EXT3 FS on sda1, internal journal
Aug  2 11:56:53 dustman-laptop kernel: [   60.032228] EXT3-fs: mounted filesystem with ordered data mode.
Aug  2 11:56:53 dustman-laptop kernel: [   60.615523] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug  2 11:56:53 dustman-laptop kernel: [   60.949515] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-E30N  UE01 PQ: 0 ANSI: 0
Aug  2 11:56:53 dustman-laptop kernel: [   60.949861] scsi 2:0:0:0: Attached scsi generic sg1 type 5
Aug  2 11:56:53 dustman-laptop kernel: [   60.983040] Driver 'sr' needs updating - please use bus_type methods
Aug  2 11:56:53 dustman-laptop kernel: [   61.018609] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Aug  2 11:56:53 dustman-laptop kernel: [   61.264456] No dock devices found.
Aug  2 11:56:54 dustman-laptop kernel: [   62.593975] apm: BIOS not found.
Aug  2 11:56:54 dustman-laptop kernel: [   62.826150] ppdev: user-space parallel port driver
Aug  2 11:56:54 dustman-laptop kernel: [   63.024979] audit(1217667414.709:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5020 profile="/usr/sbin/cupsd" namespace="default"
Aug  2 11:56:55 dustman-laptop dhcdbd: Started up.
Aug  2 11:56:56 dustman-laptop kernel: [   65.265613] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Aug  2 11:56:57 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Aug  2 11:56:59 dustman-laptop kernel: [   67.392618] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 22
Aug  2 11:57:00 dustman-laptop kernel: [   68.676407] NET: Registered protocol family 17
Aug  2 11:57:01 dustman-laptop kernel: [   70.220852] [fglrx] GART Table is not in FRAME_BUFFER range
Aug  2 11:57:01 dustman-laptop kernel: [   70.220868] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Aug  2 11:57:01 dustman-laptop kernel: [   70.220871] [fglrx] Reserve Block - 1 offset =  0Xfff5000 length = 0Xb000
Aug  2 11:57:02 dustman-laptop kernel: [   70.405909] [fglrx] interrupt source 10000000 successfully enabled
Aug  2 11:57:02 dustman-laptop kernel: [   70.405918] [fglrx] enable ID = 0x00000004
Aug  2 11:57:02 dustman-laptop kernel: [   70.406299] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Aug  2 11:57:04 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Aug  2 11:57:04 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Aug  2 11:57:04 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Aug  2 11:57:04 dustman-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Aug  2 11:57:06 dustman-laptop kernel: [   74.442910] NET: Registered protocol family 10
Aug  2 11:57:06 dustman-laptop kernel: [   74.443460] lo: Disabled Privacy Extensions
Aug  2 11:57:09 dustman-laptop kernel: [   78.197756] hda-intel: Invalid position buffer, using LPIB read method instead.
Aug  2 11:58:36 dustman-laptop pulseaudio[5659]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug  2 11:58:36 dustman-laptop pulseaudio[5659]: alsa-util.c: Unable to load mixer: No such file or directory
Aug  2 11:58:36 dustman-laptop pulseaudio[5659]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug  2 11:58:36 dustman-laptop pulseaudio[5659]: alsa-util.c: Unable to load mixer: No such file or directory
Aug  2 12:01:13 dustman-laptop kernel: [  322.226268] hdc: request sense failure: status=0x59 { DriveReady SeekComplete DataRequest Error }
Aug  2 12:01:13 dustman-laptop kernel: [  322.226280] hdc: request sense failure: error=0x40 { LastFailedSense=0x04 }
Aug  2 12:01:14 dustman-laptop kernel: [  323.307397] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 12:10:06 dustman-laptop kernel: [  854.991888] usb 3-4: new high speed USB device using ehci_hcd and address 4
Aug  2 12:10:06 dustman-laptop kernel: [  855.180328] usb 3-4: configuration #1 chosen from 1 choice
Aug  2 12:11:14 dustman-laptop kernel: [  923.183192] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 12:21:05 dustman-laptop syslogd 1.5.0#1ubuntu1: restart.
Aug  2 12:21:14 dustman-laptop kernel: [ 1523.055386] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 12:26:05 dustman-laptop kernel: [ 1814.342202] vlc[7171]: segfault at b575f000 eip b1d71980 esp b0145ff8 error 7
Aug  2 12:26:15 dustman-laptop kernel: [ 1823.835299] vlc[7183]: segfault at b3e99000 eip b1eb3980 esp b0274ff8 error 7
Aug  2 12:31:14 dustman-laptop kernel: [ 2122.926117] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 12:41:14 dustman-laptop kernel: [ 2722.807885] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 12:51:14 dustman-laptop kernel: [ 3322.676156] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 13:01:14 dustman-laptop kernel: [ 3922.554324] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 13:11:14 dustman-laptop kernel: [ 4522.425056] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 13:21:14 dustman-laptop kernel: [ 5122.295802] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 13:31:13 dustman-laptop kernel: [ 5722.166527] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 13:38:27 dustman-laptop kernel: [ 6155.499634] cdrom: This disc doesn't have any tracks I recognize!
Aug  2 13:41:13 dustman-laptop kernel: [ 6322.037271] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 13:42:46 dustman-laptop kernel: [ 6414.211332] [fglrx] interrupt source 10000000 successfully disabled!
Aug  2 13:42:46 dustman-laptop kernel: [ 6414.211340] [fglrx] enable ID = 0x00000000
Aug  2 13:42:46 dustman-laptop kernel: [ 6414.211344] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000004
Aug  2 13:42:50 dustman-laptop kernel: [ 6418.454587] [fglrx] PCIe has already been initialized. Reinitializing ...
Aug  2 13:42:50 dustman-laptop kernel: [ 6418.476270] [fglrx] GART Table is not in FRAME_BUFFER range
Aug  2 13:42:50 dustman-laptop kernel: [ 6418.476285] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Aug  2 13:42:50 dustman-laptop kernel: [ 6418.476289] [fglrx] Reserve Block - 1 offset =  0Xfff5000 length = 0Xb000
Aug  2 13:42:50 dustman-laptop kernel: [ 6418.630431] [fglrx] interrupt source 10000000 successfully enabled
Aug  2 13:42:50 dustman-laptop kernel: [ 6418.630443] [fglrx] enable ID = 0x00000004
Aug  2 13:42:50 dustman-laptop kernel: [ 6418.630872] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Aug  2 13:43:02 dustman-laptop pulseaudio[7942]: pid.c: Stale PID file, overwriting.
Aug  2 13:43:02 dustman-laptop pulseaudio[7942]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug  2 13:43:02 dustman-laptop pulseaudio[7942]: alsa-util.c: Unable to load mixer: No such file or directory
Aug  2 13:43:02 dustman-laptop pulseaudio[7942]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Aug  2 13:43:02 dustman-laptop pulseaudio[7942]: alsa-util.c: Unable to load mixer: No such file or directory
Aug  2 13:48:01 dustman-laptop kernel: [ 6729.885256] usb 3-3: new high speed USB device using ehci_hcd and address 5
Aug  2 13:48:02 dustman-laptop kernel: [ 6730.225349] usb 3-3: configuration #1 chosen from 1 choice
Aug  2 13:48:02 dustman-laptop kernel: [ 6730.254535] scsi3 : SCSI emulation for USB Mass Storage devices
Aug  2 13:48:07 dustman-laptop kernel: [ 6735.276708] scsi 3:0:0:0: Direct-Access     USB 2.0  Flash Disk       1100 PQ: 0 ANSI: 0 CCS
Aug  2 13:48:07 dustman-laptop kernel: [ 6735.480683] sd 3:0:0:0: [sdb] 3962880 512-byte hardware sectors (2029 MB)
Aug  2 13:48:07 dustman-laptop kernel: [ 6735.565776] sd 3:0:0:0: [sdb] Write Protect is off
Aug  2 13:48:07 dustman-laptop kernel: [ 6735.828814] sd 3:0:0:0: [sdb] 3962880 512-byte hardware sectors (2029 MB)
Aug  2 13:48:07 dustman-laptop kernel: [ 6735.880587] sd 3:0:0:0: [sdb] Write Protect is off
Aug  2 13:48:07 dustman-laptop kernel: [ 6735.880602]  sdb: sdb1
Aug  2 13:48:07 dustman-laptop kernel: [ 6735.988666] sd 3:0:0:0: [sdb] Attached SCSI removable disk
Aug  2 13:48:07 dustman-laptop kernel: [ 6735.988716] sd 3:0:0:0: Attached scsi generic sg2 type 0
Aug  2 13:51:13 dustman-laptop kernel: [ 6921.920034] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 14:01:13 dustman-laptop kernel: [ 7521.786754] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 14:08:01 dustman-laptop kernel: [ 7929.006953] usb 3-3: USB disconnect, address 5
Aug  2 14:11:13 dustman-laptop kernel: [ 8121.654620] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 14:21:13 dustman-laptop kernel: [ 8721.578263] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 14:31:13 dustman-laptop kernel: [ 9321.412182] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 14:41:13 dustman-laptop kernel: [ 9921.273761] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 14:51:13 dustman-laptop kernel: [10521.152437] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 15:01:13 dustman-laptop kernel: [11121.032601] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 15:11:13 dustman-laptop kernel: [11720.901334] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 15:21:13 dustman-laptop kernel: [12320.765971] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]
Aug  2 15:31:13 dustman-laptop kernel: [12920.649845] ACPI Error (evevent-0303): No installed handler for fixed event [00000000] [20070126]

```

And btw, thanks for the quick response :)

---

### Post by rogier.de.groot on 2008-08-03
Have you tried without the 'irqpoll' option and with 'noacpi' instead? Or whatever the option to disable ACPI is...

---

### Post by dustman on 2008-08-03
well, i tried to remove "irqpoll", but after a few minutes the mouse stopped working, so it wasn't ok. Tried with "noapic", and the network card was not working :confused:. I'll have to try with "noacpi", maybe that'll work.

Thanks for the suggestion :). Any other possible solutions are most welcome!

---

### Post by dustman on 2008-08-05
well...after a few days with "noacpi" as kernel boot parameter, everything works ok :D. my mouse doesn't shut down, and the cursor movement is perfect! thanks for your help \\:D/.

Cheers!

Radu

---

### Post by dustman on 2008-08-05
:( my mouse froze just a half hour after i posted here.:shock: heeeeelp!!!

---

### Post by sinaen on 2008-08-09
hehe... reboot?

well.... i have a coordless logitech mouse and it doesnt work ok. i dont know what model it is cause i have forgotten i do not have any acpi error messages.

the only i find in dmesg is 

[   46.645940] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2:1.0/input/input4
[   46.655067] input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:10.0-2
[   46.832566] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver

not much help maybe but ill need my mouse :)

---

### Post by dustman on 2008-09-16
well...after 1 month and still no solution for this...I think I'm gonna get brain damage if I use this mouse a little longer ](*,)

Please, if anyone knows, post a solution...perhaps not a working solution, but a solution nonetheless!

Thanks in advance!

---

