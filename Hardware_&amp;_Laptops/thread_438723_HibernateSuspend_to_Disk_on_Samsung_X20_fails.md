---
title: "Hibernate/Suspend to Disk on Samsung X20 fails"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by plmayer on 2007-05-10
Hi everybody,

I have Ubuntu 7.04 more or less original installation on a Samsung X20 1730. Everything seems to work fine except for hibernation. Trying to hibernate brings the system back up in ca. 10 seconds. I have looked at the log but don't understand what's the problem - could anyone point me into the right direction? 

```

May  6 20:03:20 book gnome-power-manager: (phil) Hibernating computer because the DBUS method Hibernate() was invoked
May  6 20:03:22 book kernel: [  790.704000] ACPI: PCI interrupt for device 0000:03:05.0 disabled
May  6 20:03:22 book kernel: [  791.096000] ACPI: PCI interrupt for device 0000:03:07.0 disabled
May  6 20:03:30 book kernel: [  793.156000] Disabling non-boot CPUs ...
May  6 20:03:30 book kernel: [  793.156000] Stopping tasks ... done.
May  6 20:03:30 book kernel: [  793.632000] Shrinking memory...  ^H-^H\^H|^H/^H-^H\^Hdone (44275 pages freed)
May  6 20:03:30 book kernel: [  794.240000] Freed 177100 kbytes in 0.66 seconds (268.33 MB/s)
May  6 20:03:30 book kernel: [  794.240000] Suspending console(s)
May  6 20:03:30 book kernel: [  794.836000] ACPI: PCI interrupt for device 0000:03:09.2 disabled
May  6 20:03:30 book kernel: [  794.852000] ohci1394 does not fully support suspend and resume yet
May  6 20:03:30 book kernel: [  796.704000] [fglrx] firegl_gps_setpowerdown .
May  6 20:03:30 book kernel: [  796.736000] ACPI: PCI interrupt for device 0000:01:00.0 disabled
May  6 20:03:30 book kernel: [  796.736000] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
May  6 20:03:30 book kernel: [  796.736000] ACPI: PCI interrupt for device 0000:00:1e.2 disabled
May  6 20:03:30 book kernel: [  796.736000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
May  6 20:03:30 book kernel: [  796.752000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
May  6 20:03:30 book kernel: [  796.752000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
May  6 20:03:30 book kernel: [  796.752000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
May  6 20:03:30 book kernel: [  796.752000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
May  6 20:03:30 book kernel: [  796.752000] swsusp: critical section: 
May  6 20:03:30 book kernel: [  796.752000] swsusp: Need to copy 130875 pages
May  6 20:03:30 book kernel: [  796.752000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
May  6 20:03:30 book kernel: [  796.752000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
May  6 20:03:30 book kernel: [  796.752000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
May  6 20:03:30 book kernel: [  796.752000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
May  6 20:03:30 book kernel: [  796.768000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
May  6 20:03:30 book kernel: [  796.768000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
May  6 20:03:30 book kernel: [  796.768000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 17
May  6 20:03:30 book kernel: [  797.772000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 21
May  6 20:03:30 book kernel: [  797.772000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
May  6 20:03:30 book kernel: [  797.780000] [fglrx] firegl_gps_setpowerup .
May  6 20:03:30 book kernel: [  797.868000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[c8011000-c80117ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
May  6 20:03:30 book kernel: [  797.888000] ACPI: PCI Interrupt 0000:03:09.2[C] -> GSI 18 (level, low) -> IRQ 21
May  6 20:03:30 book kernel: [  797.892000] pnp: Device 00:08 does not support activation.
May  6 20:03:30 book kernel: [  797.892000] pnp: Device 00:09 does not support activation.
May  6 20:03:30 book kernel: [  798.564000] Restarting tasks ... done.
May  6 20:03:30 book kernel: [  798.656000] Enabling non-boot CPUs ...
May  6 20:03:30 book kernel: [  799.112000] ata1.00: ata_hpa_resize 1: sectors = 194310029, hpa_sectors = 195371568
May  6 20:03:30 book kernel: [  799.112000] ata1.00: Host Protected Area detected.
May  6 20:03:30 book kernel: [  799.112000]      current size : 194310029 sectors (99486 MB)
May  6 20:03:30 book kernel: [  799.112000]      native  size : 195371568 sectors (100030 MB)
May  6 20:03:30 book kernel: [  799.124000] ata1.00: ata_hpa_resize 1: sectors = 194310029, hpa_sectors = 195371568
May  6 20:03:30 book kernel: [  799.124000] ata1.00: Host Protected Area detected.
May  6 20:03:30 book kernel: [  799.124000]      current size : 194310029 sectors (99486 MB)
May  6 20:03:30 book kernel: [  799.124000]      native  size : 195371568 sectors (100030 MB)
May  6 20:03:30 book kernel: [  799.124000] ata1.00: configured for UDMA/33
May  6 20:03:30 book kernel: [  799.288000] ata1.01: configured for UDMA/33
May  6 20:03:30 book kernel: [  799.292000] SCSI device sda: 194310029 512-byte hdwr sectors (99487 MB)
May  6 20:03:30 book kernel: [  799.296000] sda: Write Protect is off
May  6 20:03:30 book kernel: [  799.308000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 20:03:30 book kernel: [  799.320000] SCSI device sda: 194310029 512-byte hdwr sectors (99487 MB)
May  6 20:03:30 book kernel: [  799.324000] sda: Write Protect is off
May  6 20:03:30 book kernel: [  799.344000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May  6 20:03:31 book kernel: [  799.784000] tg3.c:v3.72 (January 8, 2007)
May  6 20:03:31 book kernel: [  799.784000] ACPI: PCI Interrupt 0000:03:05.0[A] -> GSI 22 (level, low) -> IRQ 22
May  6 20:03:31 book kernel: [  799.832000] eth0: Tigon3 [partno(BCM95788A50) rev 3003 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000Base-T Ethernet 00:13:77:01:5d:54
May  6 20:03:31 book kernel: [  799.832000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[0] TSOcap[1] 
May  6 20:03:31 book kernel: [  799.832000] eth0: dma_rwctrl[763f0000] dma_mask[32-bit]
May  6 20:03:31 book kernel: [  799.848000] ieee80211: 802.11 data/management/control stack, git-1.1.13
May  6 20:03:31 book kernel: [  799.848000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
May  6 20:03:31 book kernel: [  799.852000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
May  6 20:03:31 book kernel: [  799.852000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
May  6 20:03:31 book kernel: [  799.852000] ACPI: PCI Interrupt 0000:03:07.0[A] -> GSI 20 (level, low) -> IRQ 18
May  6 20:03:31 book kernel: [  799.852000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
May  6 20:03:31 book kernel: [  800.372000] ADDRCONF(NETDEV_UP): eth0: link is not ready
May  6 20:03:31 book kernel: [  800.372000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
May  6 20:03:31 book dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
May  6 20:03:32 book kernel: [  800.872000] input: Power Button (FF) as /class/input/input8
May  6 20:03:32 book kernel: [  800.908000] ACPI: Power Button (FF) [PWRF]
May  6 20:03:32 book kernel: [  800.956000] input: Lid Switch as /class/input/input9
May  6 20:03:32 book kernel: [  801.012000] ACPI: Lid Switch [LID0]
May  6 20:03:32 book kernel: [  801.060000] input: Power Button (CM) as /class/input/input10
May  6 20:03:32 book kernel: [  801.096000] ACPI: Power Button (CM) [PWRB]
May  6 20:03:32 book kernel: [  801.148000] input: Sleep Button (CM) as /class/input/input11
May  6 20:03:32 book kernel: [  801.184000] ACPI: Sleep Button (CM) [SLPB]
May  6 20:03:33 book kernel: [  802.424000] ACPI: Transitioning device [FAN1] to D3
May  6 20:03:33 book kernel: [  802.424000] ACPI: Transitioning device [FAN1] to D3
May  6 20:03:33 book kernel: [  802.424000] ACPI: Fan [FAN1] (off)
May  6 20:03:34 book kernel: [  802.488000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
May  6 20:03:34 book kernel: [  802.488000] ACPI: Processor [CPU0] (supports 2 throttling states)
May  6 20:03:34 book kernel: [  802.488000] ACPI: Thermal Zone [THRM] (58 C)
May  6 20:03:34 book kernel: [  802.636000] ACPI: AC Adapter [ADP1] (on-line)
May  6 20:03:34 book kernel: [  802.664000] ACPI: Battery Slot [BAT1] (battery present)
May  6 20:03:44 book gnome-power-manager: (phil) An unknown error occured code='32' quark='g-exec-error-quark'
May  6 20:03:44 book gnome-power-manager: (phil) Resuming computer
May  6 20:03:44 book gnome-power-manager: (phil) hibernate failed
May  6 20:03:45 book kernel: [  813.736000] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

Thanks a lot!

-phil

---

