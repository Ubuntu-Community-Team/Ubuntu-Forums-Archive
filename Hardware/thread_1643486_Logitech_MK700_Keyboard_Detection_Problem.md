---
title: "Logitech MK700 Keyboard Detection Problem"
date: 2010-12-12
forum: Hardware
---

### Post by CiaoCiao on 2010-12-12
Ubuntu 10.04 with Logitech MK700 wireless keyboard and mouse combo.. Was working originally for some time and over the last few months this problem developed.

When I boot computer the mouse/keyboard appear to be detected, but the keyboard does not work as expected.  I can get maybe one keystroke before the keyboard stops responding...Usually I press NumLock, the NumLock indicator comes on, but then there is no more sign of life from the keyboard.  I have to disconnect the wireless receiver and reconnect before I can use the keyboard.  No problems with the mouse at all....

On an older P4 system...Connected to USB1.1 port.

Any advice? Point me in a direction? Sympathy? :( I have no idea where to start looking for a solution.  Google, search forums and I haven't found anything that appears specific to me....

Here is the log from messages.  At the end you can see I disconnect and reconnect.  This is from a clean boot.

Dec 12 00:31:29 MainPC-HF kernel: [    1.292431] ohci1394 0000:02:0b.3: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 12 00:31:29 MainPC-HF kernel: [    1.295279] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1f.2/usb2/2-1/2-1:1.0/input/input3
Dec 12 00:31:29 MainPC-HF kernel: [    1.295420] generic-usb 0003:046D:C529.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1f.2-1/input0
Dec 12 00:31:29 MainPC-HF kernel: [    1.299749] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1f.2/usb2/2-1/2-1:1.1/input/input4
Dec 12 00:31:29 MainPC-HF kernel: [    1.300417] generic-usb 0003:046D:C529.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1f.2-1/input1
Dec 12 00:31:29 MainPC-HF kernel: [    1.300467] usbcore: registered new interface driver usbhid
Dec 12 00:31:29 MainPC-HF kernel: [    1.300584] usbhid: v2.6:USB HID core driver
Dec 12 00:31:29 MainPC-HF kernel: [    1.350032] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[dc000000-dc0007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Dec 12 00:31:29 MainPC-HF kernel: [    1.602348] EXT4-fs (sda1): mounted filesystem with ordered data mode
Dec 12 00:31:29 MainPC-HF kernel: [    6.285002] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Dec 12 00:31:29 MainPC-HF kernel: [    6.285618] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Dec 12 00:31:29 MainPC-HF kernel: [    6.286242] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Dec 12 00:31:29 MainPC-HF kernel: [    6.286745] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Dec 12 00:31:29 MainPC-HF kernel: [    6.287273] sd 2:0:0:0: Attached scsi generic sg3 type 0
Dec 12 00:31:29 MainPC-HF kernel: [    6.287431] sd 2:0:0:1: Attached scsi generic sg4 type 0
Dec 12 00:31:29 MainPC-HF kernel: [    6.287586] sd 2:0:0:2: Attached scsi generic sg5 type 0
Dec 12 00:31:29 MainPC-HF kernel: [    6.287735] sd 2:0:0:3: Attached scsi generic sg6 type 0
Dec 12 00:31:29 MainPC-HF kernel: [    6.291861] sd 2:0:0:0: [sdc] Attached SCSI removable disk
Dec 12 00:31:29 MainPC-HF kernel: [    6.292607] sd 2:0:0:1: [sdd] Attached SCSI removable disk
Dec 12 00:31:29 MainPC-HF kernel: [    6.293358] sd 2:0:0:2: [sde] Attached SCSI removable disk
Dec 12 00:31:29 MainPC-HF kernel: [    6.294104] sd 2:0:0:3: [sdf] Attached SCSI removable disk
Dec 12 00:31:29 MainPC-HF kernel: [   10.910343] udev: starting version 151
Dec 12 00:31:29 MainPC-HF kernel: [   10.985800] Adding 1951736k swap on /dev/sda5.  Priority:-1 extents:1 across:1951736k 
Dec 12 00:31:29 MainPC-HF kernel: [   11.077098] lp: driver loaded but no devices found
Dec 12 00:31:29 MainPC-HF kernel: [   11.114443] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 12 00:31:29 MainPC-HF kernel: [   11.219473] Linux agpgart interface v0.103
Dec 12 00:31:29 MainPC-HF kernel: [   11.223597] agpgart-intel 0000:00:00.0: Intel i850 Chipset
Dec 12 00:31:29 MainPC-HF kernel: [   11.241380] intel_rng: FWH not detected
Dec 12 00:31:29 MainPC-HF kernel: [   11.405320] vga16fb: mapped to 0xc00a0000
Dec 12 00:31:29 MainPC-HF kernel: [   11.405415] fb0: VGA16 VGA frame buffer device
Dec 12 00:31:29 MainPC-HF kernel: [   11.459071] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
Dec 12 00:31:29 MainPC-HF kernel: [   11.799638] type=1505 audit(1292131884.994:2):  operation="profile_load" pid=540 name="/sbin/dhclient3"
Dec 12 00:31:29 MainPC-HF kernel: [   11.800227] type=1505 audit(1292131884.998:3):  operation="profile_load" pid=540 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec 12 00:31:29 MainPC-HF kernel: [   11.800524] type=1505 audit(1292131884.998:4):  operation="profile_load" pid=540 name="/usr/lib/connman/scripts/dhclient-script"
Dec 12 00:31:29 MainPC-HF kernel: [   11.925262] nvidia: module license 'NVIDIA' taints kernel.
Dec 12 00:31:29 MainPC-HF kernel: [   11.925268] Disabling lock debugging due to kernel taint
Dec 12 00:31:29 MainPC-HF kernel: [   13.449569] gameport: EMU10K1 is pci0000:02:0c.1/gameport0, io 0xb400, speed 903kHz
Dec 12 00:31:29 MainPC-HF kernel: [   13.577193] EMU10K1_Audigy 0000:02:0c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec 12 00:31:29 MainPC-HF kernel: [   13.598747] EXT4-fs (sda6): mounted filesystem with ordered data mode
Dec 12 00:31:29 MainPC-HF kernel: [   13.747910] Console: switching to colour frame buffer device 80x30
Dec 12 00:31:29 MainPC-HF kernel: [   13.756893] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 12 00:31:29 MainPC-HF kernel: [   13.756906] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Dec 12 00:31:29 MainPC-HF kernel: [   13.758404] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
Dec 12 00:31:29 MainPC-HF kernel: [   16.442785] type=1505 audit(1292131889.638:5):  operation="profile_load" pid=724 name="/usr/share/gdm/guest-session/Xsession"
Dec 12 00:31:29 MainPC-HF kernel: [   16.451258] type=1505 audit(1292131889.646:6):  operation="profile_replace" pid=725 name="/sbin/dhclient3"
Dec 12 00:31:29 MainPC-HF kernel: [   16.451832] type=1505 audit(1292131889.646:7):  operation="profile_replace" pid=725 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec 12 00:31:29 MainPC-HF kernel: [   16.462221] type=1505 audit(1292131889.658:8):  operation="profile_replace" pid=725 name="/usr/lib/connman/scripts/dhclient-script"
Dec 12 00:31:29 MainPC-HF kernel: [   16.479034] type=1505 audit(1292131889.674:9):  operation="profile_load" pid=728 name="/usr/bin/evince"
Dec 12 00:31:29 MainPC-HF kernel: [   16.527830] eth0:  setting full-duplex.
Dec 12 00:31:29 MainPC-HF kernel: [   16.531512] type=1505 audit(1292131889.726:10):  operation="profile_load" pid=728 name="/usr/bin/evince-previewer"
Dec 12 00:31:29 MainPC-HF kernel: [   16.562348] type=1505 audit(1292131889.758:11):  operation="profile_load" pid=728 name="/usr/bin/evince-thumbnailer"
Dec 12 00:31:31 MainPC-HF kernel: [   17.496963] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
Dec 12 00:31:31 MainPC-HF kernel: [   17.496982] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
Dec 12 00:31:31 MainPC-HF kernel: [   17.497007] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
Dec 12 00:31:31 MainPC-HF kernel: [   18.452333] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Dec 12 00:31:32 MainPC-HF kernel: [   19.009777] ppdev: user-space parallel port driver
Dec 12 00:32:31 MainPC-HF kernel: [   77.528073] usb 2-1: USB disconnect, address 2
Dec 12 00:32:37 MainPC-HF kernel: [   83.356074] usb 2-1: new full speed USB device using uhci_hcd and address 3
Dec 12 00:32:37 MainPC-HF kernel: [   83.544258] usb 2-1: configuration #1 chosen from 1 choice
Dec 12 00:32:37 MainPC-HF kernel: [   83.555781] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1f.2/usb2/2-1/2-1:1.0/input/input5
Dec 12 00:32:37 MainPC-HF kernel: [   83.556105] generic-usb 0003:046D:C529.0003: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:1f.2-1/input0
Dec 12 00:32:37 MainPC-HF kernel: [   83.563962] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1f.2/usb2/2-1/2-1:1.1/input/input6
Dec 12 00:32:37 MainPC-HF kernel: [   83.568504] generic-usb 0003:046D:C529.0004: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1f.2-1/input1

Thanks for any help at all....
CC

---

### Post by CiaoCiao on 2011-01-28
I have officially lost all my remaining hair, but I have a solution for anyone with the same weird problem.

For some unknown reason, my keyboard accessibility option "Only accept long key presses" was enabled after every reboot.

When I did a clean install to 10.10 from 10.04, this option was always on and I essentially couldn't use my keyboard.

Disable this option and my sanity has returned...

Cheerios...

---

