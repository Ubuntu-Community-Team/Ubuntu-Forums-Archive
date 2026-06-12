---
title: "No USB discovery in 10.04"
date: 2010-09-22
forum: Hardware
---

### Post by Neonfly on 2010-09-22
Hi guys,

I'm not new to Linux but at the end of my knowledge. ;-)

Since I had installed Kubuntu 10.04 on my pc it doesn't discovering all the plugged in USB devices I have.
I was searching around and found a lot of USB problems in 10.04 but not mine.

So the behavior of the pc i was recognizing was that he founds my keyboard and my mouse (both connected via USB) and a USB Hub.

So now i wanted to connect a webcam or a scanner (which worked with 9.10) and they even not appear at **lsusb**.

The output of dmesg isn't helpful as well, cause it brings no new output on disconnecting and connecting the usb-devices. Has someone ideas how to fix this problem?

output of lsusb:
```

...
[    0.481148] EDD information not available.
[    0.590495] Freeing initrd memory: 8141k freed
[    0.630521] ata3.00: ATA-7: Maxtor 6L250S0, BANC1G10, max UDMA/133
[    0.630578] ata3.00: 490234752 sectors, multi 16: LBA48 NCQ (not used)
[    0.670292] ata3.00: configured for UDMA/133
[    0.670501] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6L250S0   BANC PQ: 0 ANSI: 5
[    0.670779] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    0.670807] sd 2:0:0:0: [sda] 490234752 512-byte logical blocks: (251 GB/233 GiB)
[    0.670887] sd 2:0:0:0: [sda] Write Protect is off
[    0.670891] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.670931] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.671228]  sda:
[    0.675815] ata4.00: ATA-7: MAXTOR STM3250820AS, 3.AAE, max UDMA/133
[    0.675912] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.691074]  sda1 sda2 < sda5 >
[    0.713397] sd 2:0:0:0: [sda] Attached SCSI disk
[    0.759110] ata4.00: configured for UDMA/133
[    0.759259] scsi 3:0:0:0: Direct-Access     ATA      MAXTOR STM325082 3.AA PQ: 0 ANSI: 5
[    0.759486] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    0.759636] sd 3:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.759771] sd 3:0:0:0: [sdb] Write Protect is off
[    0.759824] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.759862] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.760120]  sdb:
[    0.789135] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    0.798747]  sdb1
[    0.799119] sd 3:0:0:0: [sdb] Attached SCSI disk
[    0.799197] Freeing unused kernel memory: 880k freed
[    0.799819] Write protecting the kernel read-only data: 7696k
[    0.826290] udev: starting version 151
[    0.897662] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.897757] r8169 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.897876] r8169 0000:01:00.0: setting latency timer to 64
[    0.897949]   alloc irq_desc for 27 on node -1
[    0.897952]   alloc kstat_irqs on node -1
[    0.897972] r8169 0000:01:00.0: irq 27 for MSI/MSI-X
[    0.898898] eth0: RTL8101e at 0xffffc900008c0000, 00:19:66:2c:50:d2, XID 14000000 IRQ 27
[    0.940983] usb 1-2: configuration #1 chosen from 1 choice
[    0.941643] hub 1-2:1.0: USB hub found
[    0.941959] hub 1-2:1.0: 4 ports detected
[    1.188160] EXT3-fs: INFO: recovery required on readonly filesystem.
[    1.188220] EXT3-fs: write access will be enabled during recovery.
[    1.340022] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.532984] usb 3-1: configuration #1 chosen from 1 choice
[    1.551170] usbcore: registered new interface driver hiddev
[    1.551411] usbcore: registered new interface driver usbhid
[    1.551479] usbhid: v2.6:USB HID core driver
[    1.569137] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[    1.569364] microsoft 0003:045E:00DB.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:1d.1-1/input0
[    1.593078] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input4
[    1.593285] microsoft 0003:045E:00DB.0002: input,hidraw1: USB HID v1.11 Device [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:1d.1-1/input1
[    1.776163] kjournald starting.  Commit interval 5 seconds
[    1.776185] EXT3-fs: recovery complete.
[    1.776609] EXT3-fs: mounted filesystem with ordered data mode.
[    1.810071] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    1.987917] usb 3-2: configuration #1 chosen from 1 choice
[    2.016088] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input5
[    2.016285] generic-usb 0003:093A:2500.0003: input,hidraw2: USB HID v1.10 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.1-2/input0
[   25.780361] Adding 2955920k swap on /dev/sda5.  Priority:-1 extents:1 across:2955920k 
[   25.796372] udev: starting version 151
...

```

and the output of lsusb:
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                                                                                                                                               
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                                                                                                                                               
Bus 003 Device 003: ID 093a:2500 Pixart Imaging, Inc. USB Optical Mouse                                                                                                                                                                      
Bus 003 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0                                                                                                                                                        
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                                                                                                                                               
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub                                                                                                                                                                               
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB                                                                                                                                                                      
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  

```

Could it be possible that 10.04 has problems with high speed usb-devices?

Thanks in advance,
Neonfly

---

