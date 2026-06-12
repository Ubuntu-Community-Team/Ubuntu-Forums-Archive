---
title: "USB Drive does not mount after creating a bootable USB stick on Ubuntu"
date: 2012-07-25
forum: Hardware
---

### Post by Morce on 2012-07-25
Hi,

I want to format my laptop, so i did the bootable USB stick on Ubuntu, then rebooted and the boot failed probably because the create bootable usb program failed.

Now my problem is that i cannot mount the USB Drive to format it or to make the bootable USB.
I see the USB drive at disk utility but cannot format or mount it.

```

dmesg (I removed a part of the "dmesg" command output that didn't seem to be necessary)

[  598.538408] usb 2-1.1: new high-speed USB device number 5 using ehci_hcd
[  598.667920] Initializing USB Mass Storage driver...
[  598.668142] scsi6 : usb-storage 2-1.1:1.0
[  598.668306] usbcore: registered new interface driver usb-storage
[  598.668310] USB Mass Storage support registered.
[  598.680150] usbcore: registered new interface driver uas
[  599.702556] scsi 6:0:0:0: Direct-Access     TDKMedia Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
[  599.704767] sd 6:0:0:0: Attached scsi generic sg2 type 0
[  602.437724] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 1446.610504] usb 2-1.1: USB disconnect, device number 5
[ 1472.689137] usb 2-1.1: new high-speed USB device number 6 using ehci_hcd
[ 1472.785208] scsi7 : usb-storage 2-1.1:1.0
[ 1473.821571] scsi 7:0:0:0: Direct-Access     TDKMedia Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
[ 1473.822415] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 1477.225484] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 1648.343860] usb 2-1.1: USB disconnect, device number 6
[ 1658.509523] usb 2-1.1: new high-speed USB device number 7 using ehci_hcd
[ 1658.605374] scsi8 : usb-storage 2-1.1:1.0
[ 1659.642608] scsi 8:0:0:0: Direct-Access     TDKMedia Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
[ 1659.644217] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 1662.254313] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[ 1929.759589] usb 2-1.1: USB disconnect, device number 7
[ 1938.390750] usb 2-1.1: new high-speed USB device number 8 using ehci_hcd
[ 1938.486997] scsi9 : usb-storage 2-1.1:1.0
[ 1939.523849] scsi 9:0:0:0: Direct-Access     TDKMedia Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
[ 1939.525852] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 1942.169204] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[ 1960.431591] usb 2-1.1: USB disconnect, device number 8
[ 1965.484566] usb 2-1.1: new high-speed USB device number 9 using ehci_hcd
[ 1965.656136] scsi10 : usb-storage 2-1.1:1.0
[ 1966.656961] scsi 10:0:0:0: Direct-Access     USB1107  Flash Disk       8.08 PQ: 0 ANSI: 2
[ 1966.658713] scsi 10:0:0:1: Direct-Access     USB1107  Flash Disk       8.09 PQ: 0 ANSI: 2
[ 1966.660178] sd 10:0:0:0: Attached scsi generic sg2 type 0
[ 1966.660561] sd 10:0:0:1: Attached scsi generic sg3 type 0
[ 1966.662305] sd 10:0:0:1: [sdc] 22912 512-byte logical blocks: (11.7 MB/11.1 MiB)
[ 1966.664668] sd 10:0:0:0: [sdb] 7657088 512-byte logical blocks: (3.92 GB/3.65 GiB)
[ 1966.665134] sd 10:0:0:1: [sdc] Write Protect is on
[ 1966.665144] sd 10:0:0:1: [sdc] Mode Sense: 03 00 80 00
[ 1966.665648] sd 10:0:0:0: [sdb] Write Protect is off
[ 1966.665657] sd 10:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1966.666131] sd 10:0:0:1: [sdc] No Caching mode page present
[ 1966.666140] sd 10:0:0:1: [sdc] Assuming drive cache: write through
[ 1966.666623] sd 10:0:0:0: [sdb] No Caching mode page present
[ 1966.666628] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 1966.671041] sd 10:0:0:1: [sdc] No Caching mode page present
[ 1966.671046] sd 10:0:0:1: [sdc] Assuming drive cache: write through
[ 1966.671590] sd 10:0:0:0: [sdb] No Caching mode page present
[ 1966.671598] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 1966.746817]  sdc: sdc1
[ 1967.259323]  sdb:
[ 1967.263119] sd 10:0:0:1: [sdc] No Caching mode page present
[ 1967.263131] sd 10:0:0:1: [sdc] Assuming drive cache: write through
[ 1967.263137] sd 10:0:0:1: [sdc] Attached SCSI removable disk
[ 1967.263626] sd 10:0:0:0: [sdb] No Caching mode page present
[ 1967.263633] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 1967.263636] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[ 2053.572653] WARNING! power/level is deprecated; use power/control instead
[ 2053.706054] usb 2-1.1: reset high-speed USB device number 9 using ehci_hcd
[ 2053.890236] usb 2-1.1: USB disconnect, device number 9
[ 2180.191923] usb 2-1.1: new high-speed USB device number 10 using ehci_hcd
[ 2180.287944] scsi11 : usb-storage 2-1.1:1.0
[ 2181.324830] scsi 11:0:0:0: Direct-Access     TDKMedia Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
[ 2181.326294] sd 11:0:0:0: Attached scsi generic sg2 type 0
[ 2183.540722] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[ 2475.324899] unity-2d-shell[2463]: segfault at 40 ip 0000000000000040 sp 00007fff7ea61fc8 error 14 in unity-2d-shell[400000+1c000]
[ 2511.760620] usb 2-1.1: USB disconnect, device number 10
[ 3073.000622] usb 2-1.1: new high-speed USB device number 11 using ehci_hcd
[ 3073.096807] scsi12 : usb-storage 2-1.1:1.0
[ 3074.137252] scsi 12:0:0:0: Direct-Access     TDKMedia Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
[ 3074.139791] sd 12:0:0:0: Attached scsi generic sg2 type 0
[ 3076.046109] sd 12:0:0:0: [sdb] Attached SCSI removable disk
[ 5306.161650] usb 2-1.1: USB disconnect, device number 11
[ 5373.654454] usb 2-1.1: new high-speed USB device number 12 using ehci_hcd
[ 5373.750200] scsi13 : usb-storage 2-1.1:1.0
[ 5374.787245] scsi 13:0:0:0: Direct-Access     TDKMedia Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
[ 5374.788201] sd 13:0:0:0: Attached scsi generic sg2 type 0
[ 5377.347282] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[ 5411.286716] usb 2-1.1: USB disconnect, device number 12
[ 5418.895539] usb 2-1.1: new high-speed USB device number 13 using ehci_hcd
[ 5418.991693] scsi14 : usb-storage 2-1.1:1.0
[ 5420.028698] scsi 14:0:0:0: Direct-Access     TDKMedia Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
[ 5420.031141] sd 14:0:0:0: Attached scsi generic sg2 type 0
[ 5422.433112] sd 14:0:0:0: [sdb] Attached SCSI removable disk
[ 5431.479584] usb 2-1.1: USB disconnect, device number 13
[ 5465.925653] usb 2-1.1: new high-speed USB device number 14 using ehci_hcd
[ 5466.021426] scsi15 : usb-storage 2-1.1:1.0
[ 5467.058419] scsi 15:0:0:0: Direct-Access     TDKMedia Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
[ 5467.060668] sd 15:0:0:0: Attached scsi generic sg2 type 0
[ 5469.580230] sd 15:0:0:0: [sdb] Attached SCSI removable disk
[ 5586.116985] usb 2-1.1: USB disconnect, device number 14
[ 5649.961446] usb 2-1.1: new high-speed USB device number 15 using ehci_hcd
[ 5650.056840] scsi16 : usb-storage 2-1.1:1.0
[ 5651.093848] scsi 16:0:0:0: Direct-Access     TDKMedia Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
[ 5651.095877] sd 16:0:0:0: Attached scsi generic sg2 type 0
[ 5653.575680] sd 16:0:0:0: [sdb] Attached SCSI removable disk
[ 5676.088310] usb 2-1.1: USB disconnect, device number 15

```

```

tail -c 0 -f /var/log/syslog

Jul 25 19:50:04 morce-G60JX kernel: [ 6731.402303] usb 2-1.1: new high-speed USB device number 17 using ehci_hcd
Jul 25 19:50:04 morce-G60JX kernel: [ 6731.498983] scsi18 : usb-storage 2-1.1:1.0
Jul 25 19:50:04 morce-G60JX mtp-probe: checking bus 2, device 17: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1"
Jul 25 19:50:04 morce-G60JX mtp-probe: bus: 2, device: 17 was not an MTP device
Jul 25 19:50:05 morce-G60JX kernel: [ 6732.535528] scsi 18:0:0:0: Direct-Access     TDKMedia Trans-It Drive   PMAP PQ: 0 ANSI: 0 CCS
Jul 25 19:50:05 morce-G60JX kernel: [ 6732.538175] sd 18:0:0:0: Attached scsi generic sg2 type 0
Jul 25 19:50:08 morce-G60JX kernel: [ 6734.828500] sd 18:0:0:0: [sdb] Attached SCSI removable disk

```

```

lsusb (before inserting USB)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b106 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 002 Device 004: ID 046d:c316 Logitech, Inc. HID-Compliant Keyboard


lsusb (after inserting USB)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b106 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 002 Device 004: ID 046d:c316 Logitech, Inc. HID-Compliant Keyboard
Bus 002 Device 016: ID 0718:0623 Imation Corp. 


```


Thank you in advance.
Morce

---

