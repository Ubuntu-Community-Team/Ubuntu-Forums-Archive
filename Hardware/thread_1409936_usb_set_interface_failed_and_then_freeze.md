---
title: "usb_set_interface failed and then freeze"
date: 2010-02-18
forum: Hardware
---

### Post by kubu88 on 2010-02-18
I'm afflicted by persistent freeze often when I use firefox,watching video and listen to music. I thought was a problem of video card but after check kern.log I think it's something between audio server and my Edirol UA25 usb sound card. This is the kern.log error:

```
eb 18 10:01:58 luca-desktop kernel: [    1.649788] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
Feb 18 10:01:58 luca-desktop kernel: [    1.649970] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:12/device:13/input/input3
Feb 18 10:01:58 luca-desktop kernel: [    1.650002] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
Feb 18 10:01:58 luca-desktop kernel: [    1.653999] FDC 0 is a post-1991 82077
Feb 18 10:01:58 luca-desktop kernel: [    1.702175] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:26:18:e4:9d:5c
Feb 18 10:01:58 luca-desktop kernel: [    1.702178] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt gbit lnktim msi desc-v3
Feb 18 10:01:58 luca-desktop kernel: [    1.804099] usb 3-3: configuration #1 chosen from 1 choice
Feb 18 10:01:58 luca-desktop kernel: [    1.810152] usbcore: registered new interface driver hiddev
Feb 18 10:01:58 luca-desktop kernel: [    1.816172] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb3/3-3/3-3:1.0/input/input4
Feb 18 10:01:58 luca-desktop kernel: [    1.816214] generic-usb 0003:046D:C03E.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-3/input0
Feb 18 10:01:58 luca-desktop kernel: [    1.816223] usbcore: registered new interface driver usbhid
Feb 18 10:01:58 luca-desktop kernel: [    1.816224] usbhid: v2.6:USB HID core driver
Feb 18 10:01:58 luca-desktop kernel: [    2.300017] usb 4-1: new full speed USB device using ohci_hcd and address 2
Feb 18 10:01:58 luca-desktop kernel: [    2.504384] PM: Starting manual resume from disk
Feb 18 10:01:58 luca-desktop kernel: [    2.504387] PM: Resume from partition 8:6
Feb 18 10:01:58 luca-desktop kernel: [    2.504388] PM: Checking hibernation image.
Feb 18 10:01:58 luca-desktop kernel: [    2.504534] PM: Resume from disk failed.
Feb 18 10:01:58 luca-desktop kernel: [    2.516609] EXT4-fs (sda5): barriers enabled
Feb 18 10:01:58 luca-desktop kernel: [    2.524137] usb 4-1: configuration #1 chosen from 1 choice
Feb 18 10:01:58 luca-desktop kernel: [    2.539493] kjournald2 starting: pid 457, dev sda5:8, commit interval 5 seconds
Feb 18 10:01:58 luca-desktop kernel: [    2.539501] EXT4-fs (sda5): delayed allocation enabled
Feb 18 10:01:58 luca-desktop kernel: [    2.539504] EXT4-fs: file extents enabled
Feb 18 10:01:58 luca-desktop kernel: [    2.560442] EXT4-fs: mballoc enabled
Feb 18 10:01:58 luca-desktop kernel: [    2.560452] EXT4-fs (sda5): mounted filesystem with ordered data mode
Feb 18 10:01:58 luca-desktop kernel: [    2.829518] usb 4-3: new low speed USB device using ohci_hcd and address 3
Feb 18 10:01:58 luca-desktop kernel: [    2.940542] type=1505 audit(1266487312.275:2): operation="profile_load" pid=480 name=/usr/share/gdm/guest-session/Xsession
Feb 18 10:01:58 luca-desktop kernel: [    2.942386] type=1505 audit(1266487312.276:3): operation="profile_load" pid=481 name=/sbin/dhclient3
Feb 18 10:01:58 luca-desktop kernel: [    2.942568] type=1505 audit(1266487312.276:4): operation="profile_load" pid=481 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Feb 18 10:01:58 luca-desktop kernel: [    2.942671] type=1505 audit(1266487312.276:5): operation="profile_load" pid=481 name=/usr/lib/connman/scripts/dhclient-script
Feb 18 10:01:58 luca-desktop kernel: [    2.967917] type=1505 audit(1266487312.300:6): operation="profile_load" pid=482 name=/usr/bin/evince
Feb 18 10:01:58 luca-desktop kernel: [    2.970801] type=1505 audit(1266487312.304:7): operation="profile_load" pid=482 name=/usr/bin/evince-previewer
Feb 18 10:01:58 luca-desktop kernel: [    2.972541] type=1505 audit(1266487312.304:8): operation="profile_load" pid=482 name=/usr/bin/evince-thumbnailer
Feb 18 10:01:58 luca-desktop kernel: [    2.992074] type=1505 audit(1266487312.324:9): operation="profile_load" pid=484 name=/usr/lib/cups/backend/cups-pdf
Feb 18 10:01:58 luca-desktop kernel: [    2.992295] type=1505 audit(1266487312.324:10): operation="profile_load" pid=484 name=/usr/sbin/cupsd
Feb 18 10:01:58 luca-desktop kernel: [    3.062154] usb 4-3: configuration #1 chosen from 1 choice
Feb 18 10:01:58 luca-desktop kernel: [    3.072229] input: MOSART Semi. Wireless Keyboard & Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-3/4-3:1.0/input/input5
Feb 18 10:01:58 luca-desktop kernel: [    3.072269] generic-usb 0003:062A:0102.0002: input,hidraw1: USB HID v1.10 Keyboard [MOSART Semi. Wireless Keyboard & Mouse] on usb-0000:00:04.0-3/input0
Feb 18 10:01:58 luca-desktop kernel: [    3.082322] input: MOSART Semi. Wireless Keyboard & Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-3/4-3:1.1/input/input6
Feb 18 10:01:58 luca-desktop kernel: [    3.082383] generic-usb 0003:062A:0102.0003: input,hiddev96,hidraw2: USB HID v1.10 Mouse [MOSART Semi. Wireless Keyboard & Mouse] on usb-0000:00:04.0-3/input1
Feb 18 10:01:58 luca-desktop kernel: [    8.902253] udev: starting version 147
Feb 18 10:01:58 luca-desktop kernel: [    8.917937] Adding 5654840k swap on /dev/sda6.  Priority:-1 extents:1 across:5654840k 
Feb 18 10:01:58 luca-desktop kernel: [    8.918404] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600
Feb 18 10:01:58 luca-desktop kernel: [    8.918409] ACPI: I/O resource nForce2_smbus [0x700-0x73f] conflicts with ACPI region SM00 [0x700-0x73f]
Feb 18 10:01:58 luca-desktop kernel: [    8.918412] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Feb 18 10:01:58 luca-desktop kernel: [    8.918414] nForce2_smbus 0000:00:01.1: Error probing SMB2.
Feb 18 10:01:58 luca-desktop kernel: [    8.922279] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb 18 10:01:58 luca-desktop kernel: [    8.926230] lp: driver loaded but no devices found
Feb 18 10:01:58 luca-desktop kernel: [    8.926586] Linux agpgart interface v0.103
Feb 18 10:01:58 luca-desktop kernel: [    8.975872] nvidia: module license 'NVIDIA' taints kernel.
Feb 18 10:01:58 luca-desktop kernel: [    8.975875] Disabling lock debugging due to kernel taint
Feb 18 10:01:58 luca-desktop kernel: [    8.983313] parport_pc 00:05: reported by Plug and Play ACPI
Feb 18 10:01:58 luca-desktop kernel: [    8.983360] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Feb 18 10:01:58 luca-desktop kernel: [    8.988938] ppdev: user-space parallel port driver
Feb 18 10:01:58 luca-desktop kernel: [    8.992061] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb 18 10:01:58 luca-desktop kernel: [    9.035950] EXT4-fs (sda5): internal journal on sda5:8
Feb 18 10:01:58 luca-desktop kernel: [    9.045458] usbcore: registered new interface driver snd-usb-audio
Feb 18 10:01:58 luca-desktop kernel: [    9.072623] lp0: using parport0 (interrupt-driven).
Feb 18 10:01:58 luca-desktop kernel: [    9.118440] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
Feb 18 10:01:58 luca-desktop kernel: [    9.118723] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
Feb 18 10:01:58 luca-desktop kernel: [    9.118727] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
Feb 18 10:01:58 luca-desktop kernel: [    9.118742] HDA Intel 0000:00:07.0: setting latency timer to 64
Feb 18 10:01:58 luca-desktop kernel: [    9.228031] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 20
Feb 18 10:01:58 luca-desktop kernel: [    9.228035] nvidia 0000:02:00.0: PCI INT A -> Link[SGRU] -> GSI 20 (level, low) -> IRQ 20
Feb 18 10:01:58 luca-desktop kernel: [    9.228039] nvidia 0000:02:00.0: setting latency timer to 64
Feb 18 10:01:58 luca-desktop kernel: [    9.228188] NVRM: loading NVIDIA UNIX x86 Kernel Module  190.53  Tue Dec  8 18:51:41 PST 2009
Feb 18 10:01:58 luca-desktop kernel: [    9.347730]   alloc irq_desc for 27 on node -1
Feb 18 10:01:58 luca-desktop kernel: [    9.347733]   alloc kstat_irqs on node -1
Feb 18 10:01:58 luca-desktop kernel: [    9.347741] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
Feb 18 10:01:58 luca-desktop kernel: [    9.349174] __ratelimit: 3 callbacks suppressed
Feb 18 10:01:58 luca-desktop kernel: [    9.349177] type=1505 audit(1266483718.683:12): operation="profile_replace" pid=1020 name=/usr/share/gdm/guest-session/Xsession
Feb 18 10:01:58 luca-desktop kernel: [    9.358809] type=1505 audit(1266483718.691:13): operation="profile_replace" pid=1021 name=/sbin/dhclient3
Feb 18 10:01:58 luca-desktop kernel: [    9.358994] type=1505 audit(1266483718.691:14): operation="profile_replace" pid=1021 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Feb 18 10:01:58 luca-desktop kernel: [    9.359097] type=1505 audit(1266483718.691:15): operation="profile_replace" pid=1021 name=/usr/lib/connman/scripts/dhclient-script
Feb 18 10:01:58 luca-desktop kernel: [    9.361507] type=1505 audit(1266483718.695:16): operation="profile_replace" pid=1027 name=/usr/bin/evince
Feb 18 10:01:58 luca-desktop kernel: [    9.364386] type=1505 audit(1266483718.699:17): operation="profile_replace" pid=1027 name=/usr/bin/evince-previewer
Feb 18 10:01:58 luca-desktop kernel: [    9.366136] type=1505 audit(1266483718.699:18): operation="profile_replace" pid=1027 name=/usr/bin/evince-thumbnailer
Feb 18 10:01:58 luca-desktop kernel: [    9.369307] type=1505 audit(1266483718.703:19): operation="profile_replace" pid=1030 name=/usr/lib/cups/backend/cups-pdf
Feb 18 10:01:58 luca-desktop kernel: [    9.369536] type=1505 audit(1266483718.703:20): operation="profile_replace" pid=1030 name=/usr/sbin/cupsd
Feb 18 10:01:58 luca-desktop kernel: [    9.370612] type=1505 audit(1266483718.703:21): operation="profile_replace" pid=1031 name=/usr/sbin/tcpdump
Feb 18 10:02:10 luca-desktop kernel: [   19.800007] eth0: no IPv6 routers present
Feb 18 10:12:31 luca-desktop kernel: [  640.816035] timeout: still 3 active urbs..
Feb 18 10:12:46 luca-desktop kernel: [  656.369054] 2:1:1: usb_set_interface failed
Feb 18 10:12:51 luca-desktop kernel: [  661.368180] 2:1:1: usb_set_interface failed
Feb 18 10:12:56 luca-desktop kernel: [  666.368325] 2:1:1: usb_set_interface failed
Feb 18 10:13:01 luca-desktop kernel: [  671.368470] 2:1:1: usb_set_interface failed
Feb 18 10:13:06 luca-desktop kernel: [  676.368633] 2:1:1: usb_set_interface failed
Feb 18 10:13:11 luca-desktop kernel: [  681.369760] 2:1:1: usb_set_interface failed
Feb 18 10:13:16 luca-desktop kernel: [  686.368926] 2:1:1: usb_set_interface failed
Feb 18 10:13:21 luca-desktop kernel: [  691.369068] 2:1:1: usb_set_interface failed
Feb 18 10:13:26 luca-desktop kernel: [  696.368194] 2:1:1: usb_set_interface failed
Feb 18 10:13:31 luca-desktop kernel: [  701.368340] 2:1:1: usb_set_interface failed
Feb 18 10:13:36 luca-desktop kernel: [  706.368501] 2:1:1: usb_set_interface failed
Feb 18 10:13:41 luca-desktop kernel: [  711.368647] 2:1:1: usb_set_interface failed
Feb 18 10:13:46 luca-desktop kernel: [  716.368796] 2:1:1: usb_set_interface failed
Feb 18 10:13:51 luca-desktop kernel: [  721.368939] 2:1:1: usb_set_interface failed
Feb 18 10:13:56 luca-desktop kernel: [  726.368062] 2:1:1: usb_set_interface failed
Feb 18 10:14:01 luca-desktop kernel: [  731.368210] 2:1:1: usb_set_interface failed
Feb 18 10:14:06 luca-desktop kernel: [  736.368355] 2:1:1: usb_set_interface failed
Feb 18 10:14:11 luca-desktop kernel: [  741.368512] 2:1:1: usb_set_interface failed
Feb 18 10:14:16 luca-desktop kernel: [  746.370722] 2:1:1: usb_set_interface failed
Feb 18 10:14:21 luca-desktop kernel: [  751.368811] 2:1:1: usb_set_interface failed
Feb 18 10:14:26 luca-desktop kernel: [  756.372955] 2:1:1: usb_set_interface failed
Feb 18 10:14:31 luca-desktop kernel: [  761.372080] 2:1:1: usb_set_interface failed
Feb 18 10:14:36 luca-desktop kernel: [  766.372224] 2:1:1: usb_set_interface failed
Feb 18 10:14:41 luca-desktop kernel: [  771.372369] 2:1:1: usb_set_interface failed
Feb 18 10:14:46 luca-desktop kernel: [  776.372532] 2:1:1: usb_set_interface failed
Feb 18 10:14:51 luca-desktop kernel: [  781.372678] 2:1:1: usb_set_interface failed
Feb 18 10:14:56 luca-desktop kernel: [  786.372825] 2:1:1: usb_set_interface failed
Feb 18 10:15:01 luca-desktop kernel: [  791.373953] 2:1:1: usb_set_interface failed
Feb 18 10:15:06 luca-desktop kernel: [  796.372096] 2:1:1: usb_set_interface failed
Feb 18 10:15:11 luca-desktop kernel: [  801.372241] 2:1:1: usb_set_interface failed
Feb 18 10:15:16 luca-desktop kernel: [  806.372385] 2:1:1: usb_set_interface failed
Feb 18 10:15:21 luca-desktop kernel: [  811.372544] 2:1:1: usb_set_interface failed
Feb 18 10:15:26 luca-desktop kernel: [  816.372694] 2:1:1: usb_set_interface failed
Feb 18 10:15:31 luca-desktop kernel: [  821.372839] 2:1:1: usb_set_interface failed
Feb 18 10:15:36 luca-desktop kernel: [  826.372984] 2:1:1: usb_set_interface failed
Feb 18 10:15:41 luca-desktop kernel: [  831.372112] 2:1:1: usb_set_interface failed
Feb 18 10:15:46 luca-desktop kernel: [  836.372256] 2:1:1: usb_set_interface failed
Feb 18 10:15:51 luca-desktop kernel: [  841.372401] 2:1:1: usb_set_interface failed
Feb 18 10:15:56 luca-desktop kernel: [  846.372564] 2:1:1: usb_set_interface failed
Feb 18 10:16:01 luca-desktop kernel: [  851.372710] 2:1:1: usb_set_interface failed
Feb 18 10:16:06 luca-desktop kernel: [  856.372855] 2:1:1: usb_set_interface failed
Feb 18 10:16:11 luca-desktop kernel: [  861.373000] 2:1:1: usb_set_interface failed
Feb 18 10:16:16 luca-desktop kernel: [  866.372125] 2:1:1: usb_set_interface failed
Feb 18 10:16:21 luca-desktop kernel: [  871.372270] 2:1:1: usb_set_interface failed
Feb 18 10:16:26 luca-desktop kernel: [  876.372416] 2:1:1: usb_set_interface failed
Feb 18 10:16:31 luca-desktop kernel: [  881.372575] 2:1:1: usb_set_interface failed
Feb 18 10:16:36 luca-desktop kernel: [  886.373706] 2:1:1: usb_set_interface failed
Feb 18 10:16:41 luca-desktop kernel: [  891.374007] 2:1:1: usb_set_interface failed
Feb 18 10:16:46 luca-desktop kernel: [  896.374007] 2:1:1: usb_set_interface failed
Feb 18 10:16:51 luca-desktop kernel: [  901.372140] 2:1:1: usb_set_interface failed
Feb 18 10:16:56 luca-desktop kernel: [  906.372285] 2:1:1: usb_set_interface failed
Feb 18 10:17:01 luca-desktop kernel: [  911.372431] 2:1:1: usb_set_interface failed
Feb 18 10:17:06 luca-desktop kernel: [  916.372591] 2:1:1: usb_set_interface failed
Feb 18 10:17:11 luca-desktop kernel: [  921.372738] 2:1:1: usb_set_interface failed
Feb 18 10:17:16 luca-desktop kernel: [  926.372878] 2:1:1: usb_set_interface failed
Feb 18 10:17:21 luca-desktop kernel: [  931.373029] 2:1:1: usb_set_interface failed
Feb 18 10:17:26 luca-desktop kernel: [  936.374175] 2:1:1: usb_set_interface failed
Feb 18 10:17:31 luca-desktop kernel: [  941.372299] 2:1:1: usb_set_interface failed
Feb 18 10:17:36 luca-desktop kernel: [  946.372445] 2:1:1: usb_set_interface failed
Feb 18 10:17:41 luca-desktop kernel: [  951.373609] 2:1:1: usb_set_interface failed
Feb 18 10:17:57 luca-desktop kernel: [  967.078062] 2:1:1: usb_set_interface failed
Feb 18 10:18:02 luca-desktop kernel: [  972.076189] 2:1:1: usb_set_interface failed
Feb 18 10:18:07 luca-desktop kernel: [  977.076334] 2:1:1: usb_set_interface failed
Feb 18 10:18:58 luca-desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
```

Kernel is 2.6.31-19-generic on a Kermic Koala

---

### Post by jipajapa on 2010-05-16
I have a similar problem using my logitech usb headset and my hp deskjet 6540. I presume there is some sort of USB conflict. How does one troubleshoot something like this?

---

### Post by achinton on 2010-06-13
I'd quite appreciate some pointers on this too, seems to be causing me quite a lot of kernel panics. Again, I'm using an external sound card.

Info about my setup: Linux kernel version 2.6.32-22-generic, running Lucid on a Dell laptop. The external sound card in question is a Terratec Aureon 5.1 USB, though this doesn't seem to be an issue limited to any one set of hardware...

I'm not finding much in the way of stack traces from this problem, unfortunately.

---

