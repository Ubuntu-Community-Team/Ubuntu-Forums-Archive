---
title: "slow wakeup after STR"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by zorglab on 2007-05-07
Hello everybody,

I know this has been posted over and over, but I never found an answer to this specific problem.

When suspending to ram for a short period of time, everything works fine. But if I leave the computer suspended for a longer period, it takes approx. 5 minutes to wake up. During these 5 minutes, the cpu fan goes like crazy, nothing appears on the screen and the hard disk is constantly used for some time at the beginning.

I have an asus z71v running Feisty (nvidia GeForce Go 6600 with proprietary drivers, but last time I checked with edgy, nv didn't work better).

Here is the relevant part of /var/log/messages, but I can't directly see what's wrong:
```
May  6 17:27:12 ubuntu gnome-power-manager: (zorglab) Suspending computer because the suspend button has been pressed
May  6 17:27:13 ubuntu kernel: [  240.160000] skge eth0: disabling interface
May  6 17:27:13 ubuntu kernel: [  240.432000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
May  6 17:27:14 ubuntu kernel: [  240.700000] ACPI: PCI interrupt for device 0000:03:03.0 disabled
May  6 19:07:57 ubuntu kernel: [  244.088000] Stopping tasks ... done.
May  6 19:07:57 ubuntu kernel: [  244.512000] Suspending console(s)
May  6 19:07:57 ubuntu kernel: [  246.276000] ohci1394 does not fully support suspend and resume yet
May  6 19:07:57 ubuntu kernel: [  246.276000] ieee1394: hpsb_bus_reset called while bus reset already in progress
May  6 19:07:57 ubuntu kernel: [  246.296000] NVRM: RmPowerManagement: 3
May  6 19:07:57 ubuntu kernel: [  247.112000] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
May  6 19:07:57 ubuntu kernel: [  247.112000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
May  6 19:07:57 ubuntu kernel: [  247.128000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
May  6 19:07:57 ubuntu kernel: [  247.128000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
May  6 19:07:57 ubuntu kernel: [  247.128000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
May  6 19:07:57 ubuntu kernel: [  247.128000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
May  6 19:07:57 ubuntu kernel: [  247.136000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
May  6 19:07:57 ubuntu kernel: [ 5961.200000] ACPI: Transitioning device [FN00] to D3
May  6 19:07:57 ubuntu kernel: [ 5961.200000] ACPI: Transitioning device [FN00] to D3
May  6 19:07:57 ubuntu kernel: [ 5961.216000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
May  6 19:07:57 ubuntu kernel: [ 5961.288000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
May  6 19:07:57 ubuntu kernel: [ 5961.288000] usb usb1: root hub lost power or was reset
May  6 19:07:57 ubuntu kernel: [ 5961.288000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
May  6 19:07:57 ubuntu kernel: [ 5961.288000] usb usb2: root hub lost power or was reset
May  6 19:07:57 ubuntu kernel: [ 5961.288000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
May  6 19:07:57 ubuntu kernel: [ 5961.288000] usb usb3: root hub lost power or was reset
May  6 19:07:57 ubuntu kernel: [ 5961.288000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
May  6 19:07:57 ubuntu kernel: [ 5961.288000] usb usb4: root hub lost power or was reset
May  6 19:07:57 ubuntu kernel: [ 5961.304000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
May  6 19:07:57 ubuntu kernel: [ 5961.304000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
May  6 19:07:57 ubuntu kernel: [ 5961.308000] NVRM: RmPowerManagement: 4
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [update_process_times+40/112] update_process_times+0x28/0x70
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [timer_interrupt+74/176] timer_interrupt+0x4a/0xb0
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [handle_edge_irq+119/240] handle_edge_irq+0x77/0xf0
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [do_IRQ+64/128] do_IRQ+0x40/0x80
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [profile_tick+62/128] profile_tick+0x3e/0x80
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [common_interrupt+35/48] common_interrupt+0x23/0x30
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f91578b2>] _nv002720rm+0x12/0x1c [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f92d7ac0>] _nv005696rm+0x20/0x28 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f9260bec>] _nv000442rm+0x24/0x28 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f9260bbf>] _nv000491rm+0x1f/0x28 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f925615e>] _nv000489rm+0x2a/0x4c [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f9256171>] _nv000489rm+0x3d/0x4c [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f937f110>] _nv004544rm+0x2c/0x60 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f937f136>] _nv004544rm+0x52/0x60 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f93a71c0>] _nv001095rm+0x28/0x1a4 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f93808a1>] _nv004535rm+0x29/0x38 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f93a71c0>] _nv001095rm+0x28/0x1a4 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f937dbd7>] _nv004494rm+0x67/0xa0 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f937dbc1>] _nv004494rm+0x51/0xa0 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f9381e0b>] _nv004496rm+0x19f/0x1f8 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f93825e7>] _nv004499rm+0x57/0x90 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f937e6b2>] _nv004495rm+0x52/0x78 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f939b64e>] _nv001256rm+0x9a/0xec [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f939b65d>] _nv001256rm+0xa9/0xec [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f9144eb1>] _nv002933rm+0x1d/0x2c [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f939a952>] _nv001231rm+0x12/0x18 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f93951cc>] _nv001169rm+0x60/0x11c [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f93951fa>] _nv001169rm+0x8e/0x11c [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f926182a>] _nv000505rm+0x1a/0x28 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f93953ff>] _nv001196rm+0x17/0x3c [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f9187b32>] _nv009633rm+0xa2/0xd8 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f92db4b3>] _nv005740rm+0x187/0x194 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f92db4a1>] _nv005740rm+0x175/0x194 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f9144eb1>] _nv002933rm+0x1d/0x2c [nvidia]
May  6 19:07:57 ubuntu kernel: [I never got any  5971.204000]  [<f9144eba>] _nv002933rm+0x26/0x2c [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f92dbd95>] _nv005689rm+0x1d9/0xb04 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f915a34d>] _nv001987rm+0x55/0x1ac [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f915a45c>] _nv001987rm+0x164/0x1ac [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f915e685>] rm_power_management+0xb1/0x15c [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f915e706>] rm_power_management+0x132/0x15c [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f93d990f>] nv_power_management+0xcd/0x119 [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [<f93d9965>] nv_kern_resume+0xa/0xc [nvidia]
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [pci_device_resume+31/112] pci_device_resume+0x1f/0x70
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [resume_device+167/416] resume_device+0xa7/0x1a0
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [dpm_resume+174/208] dpm_resume+0xae/0xd0
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [device_resume+34/64] device_resume+0x22/0x40
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [enter_state+319/464] enter_state+0x13f/0x1d0
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [state_store+177/192] state_store+0xb1/0xc0
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [state_store+0/192] state_store+0x0/0xc0
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [subsys_attr_store+41/64] subsys_attr_store+0x29/0x40
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [sysfs_write_file+158/256] sysfs_write_file+0x9e/0x100
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [vfs_write+190/400] vfs_write+0xbe/0x190
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [sysfs_write_file+0/256] sysfs_write_file+0x0/0x100
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [sys_write+65/112] sys_write+0x41/0x70
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  [__unix_find_socket_byname+3/112] __unix_find_socket_byname+0x3/0x70
May  6 19:07:57 ubuntu kernel: [ 5971.204000]  =======================
May  6 19:07:57 ubuntu kernel: [ 5997.836000] ATA: abnormal status 0x7F on port 0x00010177
May  6 19:07:57 ubuntu kernel: [ 6005.964000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[feafb800-feafbfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
May  6 19:07:57 ubuntu kernel: [ 6006.804000] ata1: soft resetting port
May  6 19:07:57 ubuntu kernel: [ 6006.804000] Restarting tasks ... <6>usb 1-1: USB disconnect, address 5
May  6 19:07:57 ubuntu kernel: [ 6006.840000] done.
May  6 19:07:57 ubuntu kernel: [ 6007.044000] usb 1-1: new low speed USB device using uhci_hcd and address 6
May  6 19:07:57 ubuntu gnome-power-manager: (zorglab) DBUS timed out, but recovering
May  6 19:07:57 ubuntu gnome-power-manager: (zorglab) Resuming computer
May  6 19:07:58 ubuntu kernel: [ 6007.220000] usb 1-1: configuration #1 chosen from 1 choice
May  6 19:07:58 ubuntu kernel: [ 6007.252000] input: Logitech USB Receiver as /class/input/input14
May  6 19:07:58 ubuntu kernel: [ 6007.252000] input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
May  6 19:07:58 ubuntu kernel: [ 6007.284000] input: Logitech USB Receiver as /class/input/input15
May  6 19:07:58 ubuntu kernel: [ 6007.284000] input,hiddev96: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1
May  6 19:07:58 ubuntu kernel: [ 6007.360000] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
May  6 19:07:58 ubuntu kernel: [ 6007.416000] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
May  6 19:07:58 ubuntu kernel: [ 6007.416000] ata1.00: configured for UDMA/33
May  6 19:07:58 ubuntu kernel: [ 6007.416000] ata1: EH pending after completion, repeating EH (cnt=4)
May  6 19:07:58 ubuntu kernel: [ 6007.416000] ata1: soft resetting port
May  6 19:07:58 ubuntu kernel: [ 6007.744000] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
May  6 19:07:58 ubuntu kernel: [ 6007.752000] ata1.00: ata_hpa_resize 1: sectors = 156368016, hpa_sectors = 156368016
May  6 19:07:58 ubuntu kernel: [ 6007.752000] ata1.00: configured for UDMA/33
May  6 19:07:58 ubuntu kernel: [ 6007.932000] ata1.01: configured for UDMA/33
May  6 19:07:58 ubuntu kernel: [ 6007.932000] ata1: EH complete
May  6 19:07:58 ubuntu kernel: [ 6007.936000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
May  6 19:07:58 ubuntu kernel: [ 6007.936000] sda: Write Protect is off
May  6 19:07:58 ubuntu kernel: [ 6007.940000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 19:07:58 ubuntu kernel: [ 6007.944000] SCSI device sda: 156368016 512-byte hdwr sectors (80060 MB)
May  6 19:07:58 ubuntu kernel: [ 6007.948000] sda: Write Protect is off
May  6 19:07:58 ubuntu kernel: [ 6007.960000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 19:07:58 ubuntu kernel: [ 6008.000000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
May  6 19:07:58 ubuntu kernel: [ 6008.000000] skge 1.9 addr 0xfeafc000 irq 16 chip Yukon-Lite rev 9
May  6 19:07:58 ubuntu kernel: [ 6008.004000] skge eth0: addr 00:13:d4:5c:4c:94
May  6 19:07:58 ubuntu kernel: [ 6008.028000] skge eth0: enabling interface
May  6 19:07:58 ubuntu kernel: [ 6008.032000] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  6 19:07:58 ubuntu kernel: [ 6008.052000] ieee80211: 802.11 data/management/control stack, git-1.1.13
May  6 19:07:58 ubuntu kernel: [ 6008.052000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
May  6 19:07:58 ubuntu kernel: [ 6008.056000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
May  6 19:07:58 ubuntu kernel: [ 6008.056000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
May  6 19:07:58 ubuntu kernel: [ 6008.056000] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 22 (level, low) -> IRQ 21
May  6 19:07:58 ubuntu kernel: [ 6008.056000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
May  6 19:07:58 ubuntu kernel: [ 6008.196000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
May  6 19:08:04 ubuntu kernel: [ 6014.988000] input: Power Button (FF) as /class/input/input16
May  6 19:08:04 ubuntu kernel: [ 6014.988000] ACPI: Power Button (FF) [PWRF]
May  6 19:08:04 ubuntu kernel: [ 6014.988000] input: Sleep Button (CM) as /class/input/input17
May  6 19:08:04 ubuntu kernel: [ 6014.988000] ACPI: Sleep Button (CM) [SLPB]
May  6 19:08:04 ubuntu kernel: [ 6014.988000] input: Lid Switch as /class/input/input18
May  6 19:08:04 ubuntu kernel: [ 6014.988000] ACPI: Lid Switch [LID]
May  6 19:08:05 ubuntu kernel: [ 6016.004000] ACPI: Transitioning device [FN00] to D3
May  6 19:08:05 ubuntu kernel: [ 6016.004000] ACPI: Transitioning device [FN00] to D3
May  6 19:08:05 ubuntu kernel: [ 6016.004000] ACPI: Fan [FN00] (off)
May  6 19:08:05 ubuntu kernel: [ 6016.016000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
May  6 19:08:05 ubuntu kernel: [ 6016.016000] ACPI: Processor [CPU1] (supports 8 throttling states)
May  6 19:08:05 ubuntu kernel: [ 6016.080000] ACPI: Thermal Zone [THRM] (38 C)
May  6 19:08:05 ubuntu kernel: [ 6016.120000] ACPI: AC Adapter [AC0] (off-line)
May  6 19:08:05 ubuntu kernel: [ 6016.196000] ACPI: Battery Slot [BAT0] (battery present)
May  6 19:08:05 ubuntu kernel: [ 6016.196000] ACPI: Battery Slot [BAT1] (battery absent)

```
FYI, I woke it up at 19:03.

Also, it didn't work on edgy nor dapper.

Any ideas or anybody with the same problem? Thanks.

---

