---
title: "My computer Crashes due to error in hard disk partition please help!"
date: 2006-01-13
forum: Hardware &amp; Laptops
---

### Post by optotron on 2006-01-13
Hi! I have recently added a ext2 patition. It usually works just fine, but somtimes my computer totally freezes so that i have to manually reboot it. On restart i get a message something like "hda6 not umounted cleenly, checking, check Failed"  (not in those words but the content's the same) anyway; what could be wrong?

Here's my dmesg. I am sorry for posting the whole text rather than just the important parts of it, but i find it somewhat hard to tell the difference ;)  
```
[4294675.186000] Attempting manual resume
[4294675.189000] swsusp: Suspend partition has wrong signature?
[4294675.268000] usbcore: registered new driver usbfs
[4294675.268000] usbcore: registered new driver hub
[4294675.269000] USB Universal Host Controller Interface driver v2.2
[4294675.269000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[4294675.269000] PCI: Via IRQ fixup for 0000:00:10.0, from 0 to 5
[4294675.269000] uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294675.331000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294675.331000] uhci_hcd 0000:00:10.0: irq 21, io base 0x00001c00
[4294675.331000] hub 1-0:1.0: USB hub found
[4294675.331000] hub 1-0:1.0: 2 ports detected
[4294675.334000] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 21
[4294675.334000] PCI: Via IRQ fixup for 0000:00:10.1, from 0 to 5
[4294675.334000] uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294675.396000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294675.396000] uhci_hcd 0000:00:10.1: irq 21, io base 0x00001c20
[4294675.396000] hub 2-0:1.0: USB hub found
[4294675.396000] hub 2-0:1.0: 2 ports detected
[4294675.399000] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
[4294675.399000] PCI: Via IRQ fixup for 0000:00:10.2, from 0 to 5
[4294675.399000] uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
[4294675.461000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294675.461000] uhci_hcd 0000:00:10.2: irq 21, io base 0x00001c40
[4294675.461000] hub 3-0:1.0: USB hub found
[4294675.461000] hub 3-0:1.0: 2 ports detected
[4294675.486000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 21
[4294675.486000] PCI: Via IRQ fixup for 0000:00:10.3, from 0 to 5
[4294675.486000] ehci_hcd 0000:00:10.3: VIA Technologies, Inc. USB 2.0
[4294675.486000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294675.486000] ehci_hcd 0000:00:10.3: irq 21, io mem 0xd0005800
[4294675.486000] ehci_hcd 0000:00:10.3: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294675.486000] hub 4-0:1.0: USB hub found
[4294675.486000] hub 4-0:1.0: 6 ports detected
[4294675.544000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294675.544000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 23
[4294675.544000] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 7
[4294675.548000] eth0: VIA Rhine II at 0x11800, 00:0a:e4:5d:3f:ba, IRQ 23.
[4294675.549000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
[4294676.500000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[4294677.601000] usbcore: registered new driver hiddev
[4294677.618000] input: USB HID v1.10 Mouse [USB Mouse              ] on usb-0000:00:10.0-1
[4294677.618000] usbcore: registered new driver usbhid
[4294677.618000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294677.966000] ACPI: CPU0 (power states: C1[C1])
[4294678.058000] ACPI: Thermal Zone [THRS] (51 C)
[4294678.151000] ACPI: Thermal Zone [THRC] (69 C)
[4294678.391000] Attempting manual resume
[4294678.414000] swsusp: Suspend partition has wrong signature?
[4294678.442000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294678.442000] EXT3-fs: write access will be enabled during recovery.
[4294684.774000] kjournald starting.  Commit interval 5 seconds
[4294684.774000] EXT3-fs: hda2: orphan cleanup on readonly fs
[4294684.774000] ext3_orphan_cleanup: deleting unreferenced inode 735214
[4294684.775000] ext3_orphan_cleanup: deleting unreferenced inode 735202
[4294684.775000] EXT3-fs: hda2: 2 orphan inodes deleted
[4294684.775000] EXT3-fs: recovery complete.
[4294684.776000] EXT3-fs: mounted filesystem with ordered data mode.
[4294686.246000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294689.499000] Adding 562204k swap on /dev/hda5.  Priority:-1 extents:1
[4294689.764000] EXT3 FS on hda2, internal journal
[4294696.653000] parport: PnPBIOS parport detected.
[4294696.653000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294696.739000] lp0: using parport0 (interrupt-driven).
[4294696.769000] mice: PS/2 mouse device common for all mice
[4294696.808000] ieee1394: Initialized config rom entry `ip1394'
[4294696.814000] SCSI subsystem initialized
[4294696.818000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294697.604000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9248b1, caps: 0x904713/0x4000
[4294697.607000] input: SynPS/2 Synaptics TouchPad on isa0060/serio4
[4294697.881000] ts: Compaq touchscreen protocol output
[4294700.015000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294701.122000] cdrom: open failed.
[4294744.591000] Linux agpgart interface v0.101 (c) Dave Jones
[4294744.760000] agpgart: Detected AGP bridge 0
[4294744.774000] agpgart: AGP aperture is 256M @ 0xe0000000
[4294746.012000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294746.047000] shpchp: shpc_init : shpc_cap_offset == 0
[4294746.047000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294746.129000] Linux Kernel Card Services
[4294746.129000]   options:  [pci] [cardbus] [pm]
[4294746.142000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294746.142000] Yenta: CardBus bridge found at 0000:00:0b.0 [1025:006e]
[4294746.142000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294746.142000] Yenta: Routing CardBus interrupts to PCI
[4294746.142000] Yenta TI: socket 0000:00:0b.0, mfunc 0x010a1b22, devctl 0x64
[4294746.363000] Yenta: ISA IRQ mask 0x0c78, PCI irq 17
[4294746.363000] Socket status: 30000006
[4294746.377000] PCI: Enabling device 0000:00:0b.1 (0000 -> 0002)
[4294746.377000] ACPI: PCI Interrupt 0000:00:0b.1[B] -> GSI 18 (level, low) -> IRQ 18
[4294746.377000] Yenta: CardBus bridge found at 0000:00:0b.1 [1025:006e]
[4294746.378000] Yenta: Using CSCINT to route CSC interrupts to PCI
[4294746.378000] Yenta: Routing CardBus interrupts to PCI
[4294746.378000] Yenta TI: socket 0000:00:0b.1, mfunc 0x010a1b22, devctl 0x64
[4294746.599000] Yenta: ISA IRQ mask 0x0c78, PCI irq 18
[4294746.599000] Socket status: 30000006
[4294746.819000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294746.819000] ACPI: PCI Interrupt 0000:00:0b.2[C] -> GSI 19 (level, low) -> IRQ 19
[4294746.873000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[d0005000-d00057ff]  Max Packet=[2048]
[4294747.241000] irda_init()
[4294747.241000] NET: Registered protocol family 23
[4294747.715000] via82xx: Assuming DXS channels with 48k fixed sample rate.
[4294747.715000]          Please try dxs_support=5 option
[4294747.715000]          and report if it works on your machine.
[4294747.716000]          For more details, read ALSA-Configuration.txt.
[4294747.716000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[4294747.716000] PCI: Via IRQ fixup for 0000:00:11.5, from 11 to 6
[4294747.716000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294748.131000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae4044110259b]
[4294748.825000] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 22
[4294748.825000] PCI: Via IRQ fixup for 0000:00:11.6, from 11 to 6
[4294748.826000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[4294751.120000] Real Time Clock Driver v1.12
[4294751.204000] input: PC Speaker
[4294752.204000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294752.246000] NET: Registered protocol family 17
[4294758.679000] NET: Registered protocol family 10
[4294758.679000] Disabled Privacy Extensions on device c02eb280(lo)
[4294758.679000] IPv6 over IPv4 tunneling driver
[4294761.342000] ACPI: AC Adapter [AC] (on-line)
[4294761.432000] ACPI: Battery Slot [BAT0] (battery present)
[4294761.452000] ACPI: Power Button (FF) [PWRF]
[4294761.452000] ACPI: Lid Switch [LID]
[4294761.452000] ACPI: Sleep Button (CM) [SLPB]
[4294761.560000] ibm_acpi: ec object not found
[4294761.678000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[4294767.006000] apm: BIOS not found.
[4294767.938000] cs: IO port probe 0x100-0x4ff: clean.
[4294767.941000] cs: IO port probe 0x100-0x4ff: clean.
[4294767.943000] cs: IO port probe 0xc00-0xcf7: clean.
[4294767.944000] cs: IO port probe 0xc00-0xcf7: clean.
[4294767.945000] cs: IO port probe 0xa00-0xaff: clean.
[4294767.946000] cs: IO port probe 0xa00-0xaff: clean.
[4294768.243000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[4294768.243000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x6 (1400 mV)
[4294768.243000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x18 (950 mV)
[4294768.243000] cpu_init done, current fid 0x8, vid 0x4
[4294768.259000] powernow-k8: ph2 null fid transition 0x8
[4294768.585000] Bluetooth: Core ver 2.7
[4294768.585000] NET: Registered protocol family 31
[4294768.585000] Bluetooth: HCI device and connection manager initialized
[4294768.585000] Bluetooth: HCI socket layer initialized
[4294768.673000] Bluetooth: L2CAP ver 2.7
[4294768.673000] Bluetooth: L2CAP socket layer initialized
[4294768.675000] Bluetooth: RFCOMM ver 1.5
[4294768.675000] Bluetooth: RFCOMM socket layer initialized
[4294768.675000] Bluetooth: RFCOMM TTY layer initialized
[4294768.866000] eth0: no IPv6 routers present
[4295086.508000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[4295086.509000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[4295086.521000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[4295087.101000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[4295087.103000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[4295087.114000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[4295207.846000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295207.846000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295298.082000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295298.082000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295298.362000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295298.362000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295299.191000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295299.191000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295299.369000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295299.369000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295300.098000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295300.098000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295300.269000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295300.269000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295300.787000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295300.787000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295300.974000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295300.974000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295301.870000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295301.870000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295302.036000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295302.036000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295302.233000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295302.233000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295302.371000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295302.371000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295302.507000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295302.507000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295302.644000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295302.644000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295305.200000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295305.200000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295305.357000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295305.357000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295305.959000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295305.959000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295306.075000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295306.075000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295306.141000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295306.141000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295306.247000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295306.247000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295306.313000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295306.313000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295306.444000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295306.444000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295306.602000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295306.602000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295306.763000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295306.763000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295306.875000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295306.875000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295307.016000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295307.016000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295307.072000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295307.072000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295307.219000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295307.219000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295307.285000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295307.285000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295307.446000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295307.446000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295307.578000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295307.578000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295308.342000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295308.342000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
```

in case it's relevant for solving this; here's the line in fstab

/dev/hda6       /media/fancy    ext2    defaults,errors=remount-ro 0       1

Is there someone who knows what the problem might be, cause i surely don't ;)

---

