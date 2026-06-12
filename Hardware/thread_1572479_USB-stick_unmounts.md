---
title: "USB-stick unmounts"
date: 2010-09-11
forum: Hardware
---

### Post by Nonsense on 2010-09-11
I've had this problem since 9.10 and now in 10.04.
Whenever I copy files from a USB-stick (formated FAT32 or NTFS) it auto unmounts in the middle of file transfers.

I ran ```
dmesg
``` and got this:

```
[    1.879007] generic-usb 0003:046D:C03E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-5/input0
[    1.879031] usbcore: registered new interface driver usbhid
[    1.879034] usbhid: v2.6:USB HID core driver
[    1.901604] usb 2-3.1: new full speed USB device using ehci_hcd and address 4
[    2.008195] usb 2-3.1: configuration #1 chosen from 1 choice
[    2.080451] usb 2-3.2: new full speed USB device using ehci_hcd and address 5
[    2.097962] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.174935] usb 2-3.2: configuration #1 chosen from 1 choice
[    6.321917] usb-storage: device scan complete
[    6.326261] scsi 6:0:0:0: Direct-Access     Sony     USB   HS-CF Card 3.95 PQ: 0 ANSI: 0
[    6.330119] scsi 6:0:0:1: Direct-Access     Sony     USB   HS-SM Card 3.95 PQ: 0 ANSI: 0
[    6.334244] scsi 6:0:0:2: Direct-Access     Sony     USB   HS-MS Card 3.95 PQ: 0 ANSI: 0
[    6.337616] scsi 6:0:0:3: Direct-Access     Sony     USB   HS-SD Card 3.95 PQ: 0 ANSI: 0
[    6.338077] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    6.338185] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    6.338277] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    6.338368] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    6.351483] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    6.410111] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    6.414737] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    6.419366] sd 6:0:0:3: [sde] Attached SCSI removable disk
[   10.485800] udev: starting version 151
[   10.559932] i2c i2c-0: nForce2 SMBus adapter at 0x600
[   10.559949] i2c i2c-1: nForce2 SMBus adapter at 0x700
[   10.582637] Adding 8691704k swap on /dev/sda5.  Priority:-1 extents:1 across:8691704k 
[   10.588077] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   10.641725] vga16fb: initializing
[   10.641728] vga16fb: mapped to 0xc00a0000
[   10.641783] fb0: VGA16 VGA frame buffer device
[   10.650313] lp: driver loaded but no devices found
[   10.686792] Linux agpgart interface v0.103
[   10.759447] nvidia: module license 'NVIDIA' taints kernel.
[   10.759451] Disabling lock debugging due to kernel taint
[   10.798237] type=1505 audit(1284197528.695:2):  operation="profile_load" pid=677 name="/sbin/dhclient3"
[   10.798446] type=1505 audit(1284197528.695:3):  operation="profile_load" pid=677 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.798566] type=1505 audit(1284197528.695:4):  operation="profile_load" pid=677 name="/usr/lib/connman/scripts/dhclient-script"
[   11.593510] parport_pc 00:05: reported by Plug and Play ACPI
[   11.593554] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.730708] Linux video capture interface: v2.00
[   11.736357] gspca: main v2.7.0 registered
[   11.737857] gspca: probing 045e:00f7
[   11.738431] sonixj: Sonix chip id: 11
[   11.738849] gspca: probe ok
[   11.738860] gspca: probing 045e:00f7
[   11.738869] gspca: probing 045e:00f7
[   11.738906] usbcore: registered new interface driver sonixj
[   11.739432] sonixj: registered
[   11.753635] ppdev: user-space parallel port driver
[   11.780180] lp0: using parport0 (interrupt-driven).
[   11.832633] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   11.832638] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   11.832641] hda_intel: Disable MSI for Nvidia chipset
[   11.832668] HDA Intel 0000:00:07.0: setting latency timer to 64
[   11.851631] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0027
[   11.851650] usbcore: registered new interface driver usblp
[   11.854600] usbcore: registered new interface driver snd-usb-audio
[   11.893183] Console: switching to colour frame buffer device 80x30
[   12.632736] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 20
[   12.632742] nvidia 0000:00:12.0: PCI INT A -> Link[SGRU] -> GSI 20 (level, low) -> IRQ 20
[   12.632749] nvidia 0000:00:12.0: setting latency timer to 64
[   12.632753] vgaarb: device changed decodes: PCI:0000:00:12.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   12.632976] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   37.434606] type=1505 audit(1284197555.331:5):  operation="profile_load" pid=896 name="/usr/share/gdm/guest-session/Xsession"
[   37.436366] type=1505 audit(1284197555.335:6):  operation="profile_replace" pid=897 name="/sbin/dhclient3"
[   37.436586] type=1505 audit(1284197555.335:7):  operation="profile_replace" pid=897 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   37.436711] type=1505 audit(1284197555.335:8):  operation="profile_replace" pid=897 name="/usr/lib/connman/scripts/dhclient-script"
[   37.443810] type=1505 audit(1284197555.339:9):  operation="profile_load" pid=899 name="/usr/bin/evince"
[   37.446663] type=1505 audit(1284197555.343:10):  operation="profile_load" pid=899 name="/usr/bin/evince-previewer"
[   37.448623] type=1505 audit(1284197555.347:11):  operation="profile_load" pid=899 name="/usr/bin/evince-thumbnailer"
[   37.456113]   alloc irq_desc for 31 on node -1
[   37.456116]   alloc kstat_irqs on node -1
[   37.456125] forcedeth 0000:00:0a.0: irq 31 for MSI/MSI-X
[   37.465515] type=1505 audit(1284197555.363:12):  operation="profile_load" pid=964 name="/usr/lib/cups/backend/cups-pdf"
[   37.465786] type=1505 audit(1284197555.363:13):  operation="profile_load" pid=964 name="/usr/sbin/cupsd"
[   37.471709] type=1505 audit(1284197555.367:14):  operation="profile_load" pid=968 name="/usr/sbin/tcpdump"
[   37.627749] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   37.627754] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   37.627755] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   37.627756] vboxdrv: the usage of hardware performance counters by
[   37.627757] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   37.627760] vboxdrv: Found 2 processor cores.
[   37.628442] vboxdrv: fAsync=1 offMin=0x1d16c offMax=0x1d16c
[   37.628920] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   37.628922] vboxdrv: Successfully loaded version 3.2.8 (interface 0x00140001).
[   38.060346] CE: hpet increasing min_delta_ns to 15000 nsec
[   38.264495] CPU0 attaching NULL sched-domain.
[   38.264500] CPU1 attaching NULL sched-domain.
[   38.340246] CPU0 attaching sched-domain:
[   38.340250]  domain 0: span 0-1 level MC
[   38.340253]   groups: 0 1
[   38.340258] CPU1 attaching sched-domain:
[   38.340260]  domain 0: span 0-1 level MC
[   38.340262]   groups: 1 0
[   39.512053] usb 2-3.1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   39.815832] CPU0 attaching NULL sched-domain.
[   39.815839] CPU1 attaching NULL sched-domain.
[   39.836083] CPU0 attaching sched-domain:
[   39.836088]  domain 0: span 0-1 level MC
[   39.836090]   groups: 0 1
[   39.836096] CPU1 attaching sched-domain:
[   39.836097]  domain 0: span 0-1 level MC
[   39.836099]   groups: 1 0
[   47.912188] eth0: no IPv6 routers present
[  619.230421] operapluginwrap[1942]: segfault at 0 ip (null) sp bf957d0c error 14 in operapluginwrapper[8048000+2b000]
[  619.244573] operapluginwrap[1946]: segfault at 0 ip (null) sp bfeb00ec error 14 in operapluginwrapper[8048000+2b000]
[  619.251016] operapluginwrap[1947]: segfault at 0 ip (null) sp bfbc6f7c error 14 in operapluginwrapper[8048000+2b000]
[  619.257928] operapluginwrap[1948]: segfault at 0 ip (null) sp bf8c82fc error 14 in operapluginwrapper[8048000+2b000]
[  619.294303] operapluginwrap[1951]: segfault at 0 ip (null) sp bf9105fc error 14 in operapluginwrapper[8048000+2b000]
[  619.304406] operapluginwrap[1953]: segfault at 0 ip (null) sp bfe4548c error 14 in operapluginwrapper[8048000+2b000]
[  619.310838] operapluginwrap[1954]: segfault at 0 ip (null) sp bff2c36c error 14 in operapluginwrapper[8048000+2b000]
[  619.317322] operapluginwrap[1955]: segfault at 0 ip (null) sp bfdb379c error 14 in operapluginwrapper[8048000+2b000]
[  661.713963] operapluginwrap[2009]: segfault at 0 ip (null) sp bfff575c error 14 in operapluginwrapper[8048000+2b000]
[  661.729969] operapluginwrap[2012]: segfault at 0 ip (null) sp bfe3ee2c error 14 in operapluginwrapper[8048000+2b000]
[  661.737245] operapluginwrap[2013]: segfault at 0 ip (null) sp bf95eebc error 14 in operapluginwrapper[8048000+2b000]
[  661.744446] operapluginwrap[2014]: segfault at 0 ip (null) sp bff46f6c error 14 in operapluginwrapper[8048000+2b000]
[  661.768297] operapluginwrap[2017]: segfault at 0 ip (null) sp bf959c8c error 14 in operapluginwrapper[8048000+2b000]
[  661.779177] operapluginwrap[2019]: segfault at 0 ip (null) sp bf96139c error 14 in operapluginwrapper[8048000+2b000]
[  661.786260] operapluginwrap[2020]: segfault at 0 ip (null) sp bfcec30c error 14 in operapluginwrapper[8048000+2b000]
[  661.793015] operapluginwrap[2021]: segfault at 0 ip (null) sp bfc2538c error 14 in operapluginwrapper[8048000+2b000]
[  669.214437] operapluginwrap[2032]: segfault at 0 ip (null) sp bfac37dc error 14 in operapluginwrapper[8048000+2b000]
[  669.228861] operapluginwrap[2035]: segfault at 0 ip (null) sp bfc0b80c error 14 in operapluginwrapper[8048000+2b000]
[  669.235131] operapluginwrap[2036]: segfault at 0 ip (null) sp bf8e003c error 14 in operapluginwrapper[8048000+2b000]
[  669.241915] operapluginwrap[2037]: segfault at 0 ip (null) sp bfcf3c6c error 14 in operapluginwrapper[8048000+2b000]
[  669.263278] operapluginwrap[2040]: segfault at 0 ip (null) sp bfc6870c error 14 in operapluginwrapper[8048000+2b000]
[  669.273264] operapluginwrap[2042]: segfault at 0 ip (null) sp bfb713ac error 14 in operapluginwrapper[8048000+2b000]
[  669.279607] operapluginwrap[2043]: segfault at 0 ip (null) sp bfd2889c error 14 in operapluginwrapper[8048000+2b000]
[  669.286131] operapluginwrap[2044]: segfault at 0 ip (null) sp bf9bd19c error 14 in operapluginwrapper[8048000+2b000]
[ 1691.417352] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 2456.869638] usb 2-3.4: new high speed USB device using ehci_hcd and address 6
[ 2456.965120] usb 2-3.4: configuration #1 chosen from 1 choice
[ 2456.971815] scsi7 : SCSI emulation for USB Mass Storage devices
[ 2456.976114] usb-storage: device found at 6
[ 2456.976117] usb-storage: waiting for device to settle before scanning
[ 2461.976679] usb-storage: device scan complete
[ 2461.978795] scsi 7:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 2461.981443] sd 7:0:0:0: Attached scsi generic sg6 type 0
[ 2461.983338] sd 7:0:0:0: [sdf] 15679488 512-byte logical blocks: (8.02 GB/7.47 GiB)
[ 2461.985124] sd 7:0:0:0: [sdf] Write Protect is off
[ 2461.985129] sd 7:0:0:0: [sdf] Mode Sense: 23 00 00 00
[ 2461.985131] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[ 2461.989506] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[ 2461.989511]  sdf: sdf1
[ 2462.162382] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[ 2462.162388] sd 7:0:0:0: [sdf] Attached SCSI removable disk
[ 2502.750880] usb 2-3.4: USB disconnect, address 6
[ 2504.741537] usb 2-3.4: new high speed USB device using ehci_hcd and address 7
[ 2504.836991] usb 2-3.4: configuration #1 chosen from 1 choice
[ 2504.845256] scsi8 : SCSI emulation for USB Mass Storage devices
[ 2504.847427] usb-storage: device found at 7
[ 2504.847430] usb-storage: waiting for device to settle before scanning
[ 2509.844584] usb-storage: device scan complete
[ 2509.846791] scsi 8:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 2509.847316] sd 8:0:0:0: Attached scsi generic sg6 type 0
[ 2509.850649] sd 8:0:0:0: [sdf] 15679488 512-byte logical blocks: (8.02 GB/7.47 GiB)
[ 2509.851342] sd 8:0:0:0: [sdf] Write Protect is off
[ 2509.851345] sd 8:0:0:0: [sdf] Mode Sense: 23 00 00 00
[ 2509.851347] sd 8:0:0:0: [sdf] Assuming drive cache: write through
[ 2509.856411] sd 8:0:0:0: [sdf] Assuming drive cache: write through
[ 2509.856417]  sdf: sdf1
[ 2510.114344] sd 8:0:0:0: [sdf] Assuming drive cache: write through
[ 2510.114350] sd 8:0:0:0: [sdf] Attached SCSI removable disk
[ 2730.421631] usb 2-3.4: reset high speed USB device using ehci_hcd and address 7
[ 2736.664633] usb 2-3.4: device descriptor read/64, error -32
[ 2736.841632] usb 2-3.4: device descriptor read/64, error -32
[ 2737.021476] usb 2-3.4: reset high speed USB device using ehci_hcd and address 7
[ 2737.097464] usb 2-3.4: device descriptor read/64, error -32
[ 2737.277630] usb 2-3.4: device descriptor read/64, error -32
[ 2737.452483] usb 2-3.4: reset high speed USB device using ehci_hcd and address 7
[ 2737.860212] usb 2-3.4: device not accepting address 7, error -32
[ 2737.932480] usb 2-3.4: reset high speed USB device using ehci_hcd and address 7
[ 2738.340238] usb 2-3.4: device not accepting address 7, error -32
[ 2738.340802] sd 8:0:0:0: [sdf] Unhandled error code
[ 2738.340805] sd 8:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2738.340808] sd 8:0:0:0: [sdf] CDB: Read(10): 28 00 00 16 9e 18 00 00 f0 00
[ 2738.340816] end_request: I/O error, dev sdf, sector 1482264
[ 2738.340899] sd 8:0:0:0: [sdf] Unhandled error code
[ 2738.340901] sd 8:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2738.340904] sd 8:0:0:0: [sdf] CDB: Read(10): 28 00 00 16 9f 08 00 00 10 00
[ 2738.340910] end_request: I/O error, dev sdf, sector 1482504
[ 2738.340961] sd 8:0:0:0: [sdf] Unhandled error code
[ 2738.340962] sd 8:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2738.340965] sd 8:0:0:0: [sdf] CDB: Read(10): 28 00 00 16 9f 18 00 00 f0 00
[ 2738.340971] end_request: I/O error, dev sdf, sector 1482520
[ 2738.342176] usb 2-3.4: USB disconnect, address 7
[ 2738.561467] usb 2-3.4: new high speed USB device using ehci_hcd and address 8
[ 2738.636464] usb 2-3.4: device descriptor read/64, error -32
[ 2738.814542] usb 2-3.4: device descriptor read/64, error -32
[ 2738.989635] usb 2-3.4: new high speed USB device using ehci_hcd and address 9
[ 2739.065466] usb 2-3.4: device descriptor read/64, error -32
[ 2739.241629] usb 2-3.4: device descriptor read/64, error -32
[ 2739.417636] usb 2-3.4: new high speed USB device using ehci_hcd and address 10
[ 2739.824204] usb 2-3.4: device not accepting address 10, error -32
[ 2739.897636] usb 2-3.4: new high speed USB device using ehci_hcd and address 11
[ 2740.308038] usb 2-3.4: device not accepting address 11, error -32
[ 2740.308365] hub 2-3:1.0: unable to enumerate USB device on port 4
[ 2747.429631] usb 2-3.4: new high speed USB device using ehci_hcd and address 12
[ 2747.525123] usb 2-3.4: configuration #1 chosen from 1 choice
[ 2747.534786] scsi9 : SCSI emulation for USB Mass Storage devices
[ 2747.539373] usb-storage: device found at 12
[ 2747.539376] usb-storage: waiting for device to settle before scanning
[ 2752.536376] usb-storage: device scan complete
[ 2752.538485] scsi 9:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 2752.539034] sd 9:0:0:0: Attached scsi generic sg6 type 0
[ 2752.539834] sd 9:0:0:0: [sdf] 15679488 512-byte logical blocks: (8.02 GB/7.47 GiB)
[ 2752.541374] sd 9:0:0:0: [sdf] Write Protect is off
[ 2752.541379] sd 9:0:0:0: [sdf] Mode Sense: 23 00 00 00
[ 2752.541381] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[ 2752.547570] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[ 2752.547577]  sdf: sdf1
[ 2752.806351] sd 9:0:0:0: [sdf] Assuming drive cache: write through
[ 2752.806356] sd 9:0:0:0: [sdf] Attached SCSI removable disk
[ 2866.340473] usb 2-3.4: reset high speed USB device using ehci_hcd and address 12
[ 2872.584473] usb 2-3.4: device descriptor read/64, error -32
[ 2872.761473] usb 2-3.4: device descriptor read/64, error -32
[ 2872.936500] usb 2-3.4: reset high speed USB device using ehci_hcd and address 12
[ 2873.008525] usb 2-3.4: device descriptor read/64, error -32
[ 2873.185631] usb 2-3.4: device descriptor read/64, error -32
[ 2873.361643] usb 2-3.4: reset high speed USB device using ehci_hcd and address 12
[ 2873.768040] usb 2-3.4: device not accepting address 12, error -32
[ 2873.841476] usb 2-3.4: reset high speed USB device using ehci_hcd and address 12
[ 2874.248201] usb 2-3.4: device not accepting address 12, error -32
[ 2874.249293] sd 9:0:0:0: [sdf] Unhandled error code
[ 2874.249296] sd 9:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2874.249299] sd 9:0:0:0: [sdf] CDB: Read(10): 28 00 00 e1 0a 58 00 00 f0 00
[ 2874.249307] end_request: I/O error, dev sdf, sector 14748248
[ 2874.249532] sd 9:0:0:0: [sdf] Unhandled error code
[ 2874.249533] sd 9:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2874.249536] sd 9:0:0:0: [sdf] CDB: Read(10): 28 00 00 e1 0b 48 00 00 10 00
[ 2874.249543] end_request: I/O error, dev sdf, sector 14748488
[ 2874.249976] usb 2-3.4: USB disconnect, address 12
[ 2874.251274] sd 9:0:0:0: [sdf] Unhandled error code
[ 2874.251279] sd 9:0:0:0: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 2874.251282] sd 9:0:0:0: [sdf] CDB: Read(10): 28 00 00 e1 0b 58 00 00 f0 00
[ 2874.251290] end_request: I/O error, dev sdf, sector 14748504
[ 2874.343668] FAT: Directory bread(block 14743872) failed
[ 2874.344026] FAT: Directory bread(block 14743873) failed
[ 2874.344036] FAT: Directory bread(block 14743874) failed
[ 2874.344248] FAT: Directory bread(block 14743875) failed
[ 2874.344660] FAT: Directory bread(block 14743876) failed
[ 2874.345283] FAT: Directory bread(block 14743877) failed
[ 2874.345308] FAT: Directory bread(block 14743878) failed
[ 2874.345315] FAT: Directory bread(block 14743879) failed
[ 2874.412464] usb 2-3.4: new high speed USB device using ehci_hcd and address 13
[ 2874.484470] usb 2-3.4: device descriptor read/64, error -32
[ 2874.660478] usb 2-3.4: device descriptor read/64, error -32
[ 2874.837639] usb 2-3.4: new high speed USB device using ehci_hcd and address 14
[ 2874.913640] usb 2-3.4: device descriptor read/64, error -32
[ 2875.090253] usb 2-3.4: device descriptor read/64, error -32
[ 2875.265640] usb 2-3.4: new high speed USB device using ehci_hcd and address 15
[ 2875.672035] usb 2-3.4: device not accepting address 15, error -32
[ 2875.745626] usb 2-3.4: new high speed USB device using ehci_hcd and address 16
[ 2876.152029] usb 2-3.4: device not accepting address 16, error -32
[ 2876.152466] hub 2-3:1.0: unable to enumerate USB device on port 4
[ 2881.573633] usb 2-3.4: new high speed USB device using ehci_hcd and address 17
[ 2881.673161] usb 2-3.4: configuration #1 chosen from 1 choice
[ 2881.673446] scsi10 : SCSI emulation for USB Mass Storage devices
[ 2881.673542] usb-storage: device found at 17
[ 2881.673544] usb-storage: waiting for device to settle before scanning
[ 2886.672936] usb-storage: device scan complete
[ 2886.674786] scsi 10:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 2886.675183] sd 10:0:0:0: Attached scsi generic sg6 type 0
[ 2886.678299] sd 10:0:0:0: [sdf] 15679488 512-byte logical blocks: (8.02 GB/7.47 GiB)
[ 2886.680512] sd 10:0:0:0: [sdf] Write Protect is off
[ 2886.680517] sd 10:0:0:0: [sdf] Mode Sense: 23 00 00 00
[ 2886.680520] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[ 2886.685520] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[ 2886.685526]  sdf: sdf1
[ 2886.938350] sd 10:0:0:0: [sdf] Assuming drive cache: write through
[ 2886.938355] sd 10:0:0:0: [sdf] Attached SCSI removable disk
[ 2957.085464] usb 2-3.4: reset high speed USB device using ehci_hcd and address 17
[ 2968.332476] usb 2-3.4: device descriptor read/64, error -110
[ 2983.508473] usb 2-3.4: device descriptor read/64, error -110
[ 2983.685626] usb 2-3.4: reset high speed USB device using ehci_hcd and address 17
[ 2991.600908] sd 10:0:0:0: Device offlined - not ready after error recovery
[ 2991.600921] sd 10:0:0:0: [sdf] Unhandled error code
[ 2991.600923] sd 10:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2991.600927] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 ee 5f b0 00 00 f0 00
[ 2991.600935] end_request: I/O error, dev sdf, sector 15622064
[ 2991.600952] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.600973] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.600980] sd 10:0:0:0: [sdf] Unhandled error code
[ 2991.600982] sd 10:0:0:0: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 2991.600985] sd 10:0:0:0: [sdf] CDB: Read(10): 28 00 00 ee 60 a0 00 00 10 00
[ 2991.600991] end_request: I/O error, dev sdf, sector 15622304
[ 2991.601001] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601009] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601014] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601018] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601023] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601028] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601032] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601036] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601041] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601045] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601049] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601054] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601058] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601063] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601067] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601072] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601076] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601080] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601085] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601090] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601097] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601103] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601110] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601114] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601121] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601125] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601130] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601134] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601138] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601142] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601148] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601153] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601157] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601161] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601165] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601169] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601174] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601182] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601192] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.601352] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.604718] sd 10:0:0:0: rejecting I/O to offline device
[ 2991.604841] usb 2-3.4: USB disconnect, address 17
[ 2994.980460] usb 2-3.4: new high speed USB device using ehci_hcd and address 18
[ 2995.077239] usb 2-3.4: configuration #1 chosen from 1 choice
[ 2995.086724] scsi11 : SCSI emulation for USB Mass Storage devices
[ 2995.089625] usb-storage: device found at 18
[ 2995.089628] usb-storage: waiting for device to settle before scanning
[ 3000.088392] usb-storage: device scan complete
[ 3000.090799] scsi 11:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 3000.091274] sd 11:0:0:0: Attached scsi generic sg6 type 0
[ 3000.092850] sd 11:0:0:0: [sdf] 15679488 512-byte logical blocks: (8.02 GB/7.47 GiB)
[ 3000.094665] sd 11:0:0:0: [sdf] Write Protect is off
[ 3000.094669] sd 11:0:0:0: [sdf] Mode Sense: 23 00 00 00
[ 3000.094672] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[ 3000.098572] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[ 3000.098578]  sdf: sdf1
[ 3000.350405] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[ 3000.350410] sd 11:0:0:0: [sdf] Attached SCSI removable disk
[ 3362.992845] usb 2-3.4: reset high speed USB device using ehci_hcd and address 18
[ 3369.233634] usb 2-3.4: device descriptor read/64, error -32
[ 3369.409634] usb 2-3.4: device descriptor read/64, error -32
[ 3369.585636] usb 2-3.4: reset high speed USB device using ehci_hcd and address 18
[ 3369.661636] usb 2-3.4: device descriptor read/64, error -32
[ 3369.836470] usb 2-3.4: device descriptor read/64, error -32
[ 3370.012483] usb 2-3.4: reset high speed USB device using ehci_hcd and address 18
[ 3370.420035] usb 2-3.4: device not accepting address 18, error -32
[ 3370.493633] usb 2-3.4: reset high speed USB device using ehci_hcd and address 18
[ 3370.900140] usb 2-3.4: device not accepting address 18, error -32
[ 3370.900755] sd 11:0:0:0: [sdf] Unhandled error code
[ 3370.900758] sd 11:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3370.900761] sd 11:0:0:0: [sdf] CDB: Read(10): 28 00 00 d5 34 a8 00 00 f0 00
[ 3370.900769] end_request: I/O error, dev sdf, sector 13972648
[ 3370.901829] sd 11:0:0:0: [sdf] Unhandled error code
[ 3370.901833] sd 11:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3370.901837] sd 11:0:0:0: [sdf] CDB: Read(10): 28 00 00 d5 35 98 00 00 0c 00
[ 3370.901844] end_request: I/O error, dev sdf, sector 13972888
[ 3370.902052] sd 11:0:0:0: [sdf] Unhandled error code
[ 3370.902053] sd 11:0:0:0: [sdf] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3370.902056] sd 11:0:0:0: [sdf] CDB: Read(10): 28 00 00 d5 34 a8 00 00 80 00
[ 3370.902062] end_request: I/O error, dev sdf, sector 13972648
[ 3370.902090] usb 2-3.4: USB disconnect, address 18
[ 3371.117628] usb 2-3.4: new high speed USB device using ehci_hcd and address 19
[ 3371.192465] usb 2-3.4: device descriptor read/64, error -32
[ 3371.369631] usb 2-3.4: device descriptor read/64, error -32
[ 3371.545638] usb 2-3.4: new high speed USB device using ehci_hcd and address 20
[ 3371.620680] usb 2-3.4: device descriptor read/64, error -32
[ 3371.797634] usb 2-3.4: device descriptor read/64, error -32
[ 3371.973636] usb 2-3.4: new high speed USB device using ehci_hcd and address 21
[ 3372.380202] usb 2-3.4: device not accepting address 21, error -32
[ 3372.453650] usb 2-3.4: new high speed USB device using ehci_hcd and address 22
[ 3372.860198] usb 2-3.4: device not accepting address 22, error -32
[ 3372.860643] hub 2-3:1.0: unable to enumerate USB device on port 4
[ 3374.140124] FAT: Directory bread(block 13988360) failed
[ 3374.140133] FAT: Directory bread(block 13988361) failed
[ 3374.140139] FAT: Directory bread(block 13988362) failed
[ 3374.140145] FAT: Directory bread(block 13988363) failed
[ 3374.140151] FAT: Directory bread(block 13988364) failed
[ 3374.140156] FAT: Directory bread(block 13988365) failed
[ 3374.140162] FAT: Directory bread(block 13988366) failed
[ 3374.140168] FAT: Directory bread(block 13988367) failed
[ 3374.140178] FAT: FAT read failed (blocknr 13668)
[ 3374.141431] FAT: FAT read failed (blocknr 13668)
[ 3379.240635] usb 2-3.4: new high speed USB device using ehci_hcd and address 23
[ 3379.336992] usb 2-3.4: configuration #1 chosen from 1 choice
[ 3379.337326] scsi12 : SCSI emulation for USB Mass Storage devices
[ 3379.337422] usb-storage: device found at 23
[ 3379.337424] usb-storage: waiting for device to settle before scanning
[ 3384.336749] usb-storage: device scan complete
[ 3384.338525] scsi 12:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 3384.340012] sd 12:0:0:0: Attached scsi generic sg6 type 0
[ 3384.342147] sd 12:0:0:0: [sdf] 15679488 512-byte logical blocks: (8.02 GB/7.47 GiB)
[ 3384.343503] sd 12:0:0:0: [sdf] Write Protect is off
[ 3384.343506] sd 12:0:0:0: [sdf] Mode Sense: 23 00 00 00
[ 3384.343508] sd 12:0:0:0: [sdf] Assuming drive cache: write through
[ 3384.349507] sd 12:0:0:0: [sdf] Assuming drive cache: write through
[ 3384.349510]  sdf: sdf1
[ 3384.601361] sd 12:0:0:0: [sdf] Assuming drive cache: write through
[ 3384.601367] sd 12:0:0:0: [sdf] Attached SCSI removable disk
[ 3411.104793] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 3411.104798] ata4.00: irq_stat 0x40000000
[ 3411.104801] sr 3:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[ 3411.104811] ata4.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 3411.104812]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x1 (device error)
[ 3411.104815] ata4.00: status: { DRDY }

```

---

