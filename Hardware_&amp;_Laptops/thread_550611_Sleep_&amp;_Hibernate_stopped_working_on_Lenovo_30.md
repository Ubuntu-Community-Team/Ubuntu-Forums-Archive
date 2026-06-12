---
title: "Sleep &amp; Hibernate stopped working on Lenovo 300 N100"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by lincolnlad on 2007-09-14
Hello,

I bought a Lenovo 300 N100 with Ubuntu pre-installed from the Linux Emporium (UK).  Sleep and hibernate were working. Now after a few days 90% of the time, sleep and hibernate don't work correctly.  I think it's a problem with Gnome as when I wake it up from sleep GDM tries over and over to reload.  If I press CTL-ALT-DEL a few times, it reboots itself.  If I press CTRL-ALT-F1 a few times, I kind of get a console login but I can't actually see what I'm typing.  The machine itself seems to be waking up but the graphical environment is having problems.  I've tried uninstalling the applications I've added over the last few days but it's not made any difference.  

Any help would be much appreciated.  Thanks!

Here's some logs:

/var/log/messages showing going to sleep and waking up:

```

Sep 14 08:39:03 ubuntu gnome-power-manager: (joss) GNOME interactive logout because the power button has been pressed
Sep 14 08:39:06 ubuntu gnome-power-manager: (joss) Suspending computer because the DBUS method Suspend() was invoked
Sep 14 08:39:10 ubuntu kernel: [  102.832000] ACPI: PCI interrupt for device 0000:05:01.0 disabled
Sep 14 08:39:10 ubuntu kernel: [  102.904000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
Sep 14 08:39:12 ubuntu kernel: [  105.192000] Disabling non-boot CPUs ...
Sep 14 08:39:12 ubuntu kernel: [  105.312000] CPU 1 is now offline
Sep 14 08:39:12 ubuntu kernel: [  105.312000] SMP alternatives: switching to UP code
Sep 14 08:44:14 ubuntu kernel: [  105.316000] CPU1 is down
Sep 14 08:44:14 ubuntu kernel: [  105.316000] Stopping tasks ... done.
Sep 14 08:44:14 ubuntu kernel: [  106.364000] Suspending console(s)
Sep 14 08:44:14 ubuntu kernel: [  107.648000] ACPI: PCI interrupt for device 0000:05:06.1 disabled
Sep 14 08:44:14 ubuntu kernel: [  107.664000] ohci1394 does not fully support suspend and resume yet
Sep 14 08:44:14 ubuntu kernel: [  107.684000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Sep 14 08:44:14 ubuntu kernel: [  107.700000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Sep 14 08:44:14 ubuntu kernel: [  107.716000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Sep 14 08:44:14 ubuntu kernel: [  107.716000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Sep 14 08:44:14 ubuntu kernel: [  107.716000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Sep 14 08:44:14 ubuntu kernel: [  107.716000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Sep 14 08:44:14 ubuntu kernel: [  108.724000] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:558: hda_intel: azx_get_response timeout, switching to polling mode...
Sep 14 08:44:14 ubuntu kernel: [  108.724000] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Sep 14 08:44:14 ubuntu kernel: [  407.780000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
Sep 14 08:44:14 ubuntu kernel: [  407.796000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Sep 14 08:44:14 ubuntu kernel: [  408.008000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
Sep 14 08:44:14 ubuntu kernel: [  408.008000] usb usb2: root hub lost power or was reset
Sep 14 08:44:14 ubuntu kernel: [  408.008000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
Sep 14 08:44:14 ubuntu kernel: [  408.008000] usb usb3: root hub lost power or was reset
Sep 14 08:44:14 ubuntu kernel: [  408.008000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
Sep 14 08:44:14 ubuntu kernel: [  408.008000] usb usb4: root hub lost power or was reset
Sep 14 08:44:14 ubuntu kernel: [  408.008000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
Sep 14 08:44:14 ubuntu kernel: [  408.008000] usb usb5: root hub lost power or was reset
Sep 14 08:44:14 ubuntu kernel: [  408.024000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
Sep 14 08:44:14 ubuntu kernel: [  408.040000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
Sep 14 08:44:14 ubuntu kernel: [  408.108000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[d0100800-d0100fff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Sep 14 08:44:14 ubuntu kernel: [  408.128000] ACPI: PCI Interrupt 0000:05:06.1[B] -> GSI 23 (level, low) -> IRQ 18
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pnp: Device 00:09 does not support activation.
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pnp: Device 00:0a does not support activation.
Sep 14 08:44:14 ubuntu kernel: [  409.176000] Restarting tasks ... <6>usb 2-2: USB disconnect, address 2
Sep 14 08:44:14 ubuntu kernel: [  409.200000] ata2: EH pending after completion, repeating EH (cnt=4)
Sep 14 08:44:14 ubuntu kernel: [  409.200000] ata2: soft resetting port
Sep 14 08:44:14 ubuntu kernel: [  409.232000] done.
Sep 14 08:44:14 ubuntu kernel: [  409.232000] Enabling non-boot CPUs ...
Sep 14 08:44:14 ubuntu kernel: [  409.256000] SMP alternatives: switching to SMP code
Sep 14 08:44:14 ubuntu kernel: [  409.256000] Booting processor 1/1 eip 3000
Sep 14 08:44:14 ubuntu kernel: [  409.268000] Initializing CPU#1
Sep 14 08:44:14 ubuntu kernel: [  409.348000] Calibrating delay using timer specific routine.. 3724.27 BogoMIPS (lpj=7448550)
Sep 14 08:44:14 ubuntu kernel: [  409.348000] monitor/mwait feature present.
Sep 14 08:44:14 ubuntu kernel: [  409.348000] CPU: L1 I cache: 32K, L1 D cache: 32K
Sep 14 08:44:14 ubuntu kernel: [  409.348000] CPU: L2 cache: 2048K
Sep 14 08:44:14 ubuntu kernel: [  409.348000] CPU: Physical Processor ID: 0
Sep 14 08:44:14 ubuntu kernel: [  409.348000] CPU: Processor Core ID: 1
Sep 14 08:44:14 ubuntu kernel: [  409.348000] CPU1: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz stepping 0c
Sep 14 08:44:14 ubuntu kernel: [  409.352000] CPU1 is up
Sep 14 08:44:14 ubuntu kernel: [  409.556000] usb 4-2: USB disconnect, address 2
Sep 14 08:44:14 ubuntu gnome-power-manager: (joss) DBUS timed out, but recovering
Sep 14 08:44:14 ubuntu kernel: [  409.684000] ata2.00: configured for UDMA/33
Sep 14 08:44:14 ubuntu kernel: [  409.684000] ata2: EH complete
Sep 14 08:44:15 ubuntu kernel: [  410.328000] usb 2-2: new full speed USB device using uhci_hcd and address 3
Sep 14 08:44:15 ubuntu kernel: [  410.500000] usb 2-2: configuration #1 chosen from 1 choice
Sep 14 08:44:16 ubuntu kernel: [  410.744000] usb 4-2: new full speed USB device using uhci_hcd and address 3
Sep 14 08:44:16 ubuntu kernel: [  410.908000] usb 4-2: configuration #1 chosen from 1 choice
Sep 14 08:44:16 ubuntu kernel: [  411.072000] ata1: EH pending after completion, repeating EH (cnt=4)
Sep 14 08:44:16 ubuntu kernel: [  411.072000] ata1: soft resetting port
Sep 14 08:44:16 ubuntu kernel: [  411.240000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Sep 14 08:44:16 ubuntu kernel: [  411.248000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Sep 14 08:44:16 ubuntu kernel: [  411.248000] ata1.00: configured for UDMA/100
Sep 14 08:44:16 ubuntu kernel: [  411.248000] ata1: EH complete
Sep 14 08:44:16 ubuntu kernel: [  411.256000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Sep 14 08:44:16 ubuntu kernel: [  411.256000] sda: Write Protect is off
Sep 14 08:44:16 ubuntu kernel: [  411.276000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 14 08:44:16 ubuntu gnome-power-manager: (joss) Resuming computer
Sep 14 08:44:17 ubuntu kernel: [  412.004000] 8139too Fast Ethernet driver 0.9.28
Sep 14 08:44:17 ubuntu kernel: [  412.004000] ACPI: PCI Interrupt 0000:05:01.0[A] -> GSI 21 (level, low) -> IRQ 21
Sep 14 08:44:17 ubuntu kernel: [  412.004000] eth0: RealTek RTL8139 at 0xf8bdc000, 00:1b:38:07:db:35, IRQ 21
Sep 14 08:44:17 ubuntu kernel: [  412.012000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Sep 14 08:44:17 ubuntu kernel: [  412.012000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Sep 14 08:44:17 ubuntu kernel: [  412.020000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
Sep 14 08:44:17 ubuntu kernel: [  412.020000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Sep 14 08:44:17 ubuntu kernel: [  412.020000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
Sep 14 08:44:17 ubuntu kernel: [  412.020000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Sep 14 08:44:20 ubuntu kernel: [  412.728000] eth0: link down
Sep 14 08:44:21 ubuntu kernel: [  413.984000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Sep 14 08:44:21 ubuntu kernel: [  414.404000] input: Power Button (FF) as /class/input/input6
Sep 14 08:44:21 ubuntu kernel: [  414.404000] ACPI: Power Button (FF) [PWRF]
Sep 14 08:44:21 ubuntu kernel: [  414.404000] input: Lid Switch as /class/input/input7
Sep 14 08:44:21 ubuntu kernel: [  414.404000] ACPI: Lid Switch [LID0]
Sep 14 08:44:21 ubuntu kernel: [  414.404000] input: Power Button (CM) as /class/input/input8
Sep 14 08:44:21 ubuntu kernel: [  414.404000] ACPI: Power Button (CM) [PWRB]
Sep 14 08:44:21 ubuntu kernel: [  414.556000] ACPI Exception (acpi_thermal-0412): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
Sep 14 08:44:21 ubuntu kernel: [  414.604000] ACPI: Thermal Zone [TZ00] (36 C)
Sep 14 08:44:22 ubuntu kernel: [  414.712000] ACPI: AC Adapter [ACAD] (on-line)
Sep 14 08:44:22 ubuntu kernel: [  414.852000] ACPI: Battery Slot [BAT1] (battery present)
Sep 14 08:44:26 ubuntu gconfd (joss-6036): Received signal 15, shutting down cleanly
Sep 14 08:44:26 ubuntu gconfd (joss-6036): Exiting
Sep 14 08:44:27 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Sep 14 08:44:27 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Sep 14 08:44:27 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Sep 14 08:44:32 ubuntu gconfd (joss-7685): starting (version 2.18.0.1), pid 7685 user 'joss'
Sep 14 08:44:32 ubuntu gconfd (joss-7685): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep 14 08:44:32 ubuntu gconfd (joss-7685): Resolved address "xml:readwrite:/home/joss/.gconf" to a writable configuration source at position 1
Sep 14 08:44:32 ubuntu gconfd (joss-7685): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep 14 08:44:32 ubuntu gconfd (joss-7685): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep 14 08:44:32 ubuntu gconfd (joss-7685): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep 14 08:45:45 ubuntu exiting on signal 15
Sep 14 08:46:35 ubuntu syslogd 1.4.1#20ubuntu4: restart.

```

and here's /var/log/debug :

```


Sep 14 08:39:12 ubuntu kernel: [  105.192000] PM: Preparing system for mem sleep
Sep 14 08:44:14 ubuntu kernel: [  106.364000] iTCO_wdt iTCO_wdt: suspend
Sep 14 08:44:14 ubuntu kernel: [  106.364000] platform bluetooth: suspend
Sep 14 08:44:14 ubuntu kernel: [  106.364000] sr 1:0:0:0: suspend
Sep 14 08:44:14 ubuntu kernel: [  106.364000] sd 0:0:0:0: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.112000] usb 4-2:1.0: PM: suspend 2-->2
Sep 14 08:44:14 ubuntu kernel: [  107.112000] usb 4-2: PM: suspend 2-->2
Sep 14 08:44:14 ubuntu kernel: [  107.112000] usb 2-2:1.3: PM: suspend 2-->2
Sep 14 08:44:14 ubuntu kernel: [  107.112000] usb 2-2:1.2: PM: suspend 2-->2
Sep 14 08:44:14 ubuntu kernel: [  107.112000] hci_usb 2-2:1.1: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.112000] hci_usb 2-2:1.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.112000] usb 2-2: suspend, may wakeup
Sep 14 08:44:14 ubuntu kernel: [  107.136000] hub 5-0:1.0: PM: suspend 2-->2
Sep 14 08:44:14 ubuntu kernel: [  107.136000] usb usb5: PM: suspend 2-->2
Sep 14 08:44:14 ubuntu kernel: [  107.136000] hub 4-0:1.0: PM: suspend 2-->2
Sep 14 08:44:14 ubuntu kernel: [  107.136000] usb usb4: PM: suspend 2-->2
Sep 14 08:44:14 ubuntu kernel: [  107.136000] hub 3-0:1.0: PM: suspend 2-->2
Sep 14 08:44:14 ubuntu kernel: [  107.136000] usb usb3: PM: suspend 2-->2
Sep 14 08:44:14 ubuntu kernel: [  107.136000] hub 2-0:1.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.136000] usb usb2: suspend, may wakeup
Sep 14 08:44:14 ubuntu kernel: [  107.136000] hub 1-0:1.0: PM: suspend 2-->2
Sep 14 08:44:14 ubuntu kernel: [  107.136000] usb usb1: PM: suspend 2-->2
Sep 14 08:44:14 ubuntu kernel: [  107.136000] vesafb vesafb.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.136000] platform eisa.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.136000] i8042 i8042: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] serial8250 serial8250: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] pci_express 0000:00:1c.1:pcie02: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] pci_express 0000:00:1c.1:pcie00: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] pci_express 0000:00:1c.0:pcie02: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] pci_express 0000:00:1c.0:pcie00: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] platform pcspkr: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] i8042 aux 00:0a: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] i8042 kbd 00:09: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] pnp 00:08: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] system 00:07: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] system 00:06: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] pnp 00:05: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] pnp 00:04: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] pnp 00:03: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] pnp 00:02: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] system 00:01: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] pnp 00:00: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] pci 0000:05:06.4: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] pci 0000:05:06.3: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] pci 0000:05:06.2: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.648000] sdhci 0000:05:06.1: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.664000] ohci1394 0000:05:06.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.684000] yenta_cardbus 0000:05:04.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.684000] pci 0000:05:01.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.684000] pci 0000:03:00.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.684000] pci 0000:00:1f.3: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.684000] ata_piix 0000:00:1f.2: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.700000] pci 0000:00:1f.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.700000] pci 0000:00:1e.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.700000] ehci_hcd 0000:00:1d.7: suspend, may wakeup
Sep 14 08:44:14 ubuntu kernel: [  107.716000] uhci_hcd 0000:00:1d.3: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.716000] uhci_hcd 0000:00:1d.2: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.716000] uhci_hcd 0000:00:1d.1: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.716000] uhci_hcd 0000:00:1d.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.716000] pcieport-driver 0000:00:1c.1: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.716000] pcieport-driver 0000:00:1c.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  107.716000] HDA Intel 0000:00:1b.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] pci 0000:00:02.1: suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] pci 0000:00:02.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] agpgart-intel 0000:00:00.0: suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] acpi acpi: suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] PM: Entering mem sleep
Sep 14 08:44:14 ubuntu kernel: [  108.740000] iTCO_wdt iTCO_wdt: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] platform bluetooth: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] vesafb vesafb.0: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] platform eisa.0: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] i8042 i8042: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] serial8250 serial8250: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] platform pcspkr: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] pci 0000:05:06.4: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] pci 0000:05:06.3: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] pci 0000:05:06.2: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] sdhci 0000:05:06.1: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] ohci1394 0000:05:06.0: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] yenta_cardbus 0000:05:04.0: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] pci 0000:05:01.0: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] pci 0000:03:00.0: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] pci 0000:00:1f.3: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] pci 0000:00:1f.0: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] pci 0000:00:1e.0: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] pcieport-driver 0000:00:1c.1: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] pcieport-driver 0000:00:1c.0: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] HDA Intel 0000:00:1b.0: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] pci 0000:00:02.1: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] pci 0000:00:02.0: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] agpgart-intel 0000:00:00.0: LATE suspend
Sep 14 08:44:14 ubuntu kernel: [  108.740000] Back to C!
Sep 14 08:44:14 ubuntu kernel: [  407.740000] agpgart-intel 0000:00:00.0: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] pci 0000:00:02.0: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] pci 0000:00:02.1: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] HDA Intel 0000:00:1b.0: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] pcieport-driver 0000:00:1c.0: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] pcieport-driver 0000:00:1c.1: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] uhci_hcd 0000:00:1d.0: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] uhci_hcd 0000:00:1d.1: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] uhci_hcd 0000:00:1d.2: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] uhci_hcd 0000:00:1d.3: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] ehci_hcd 0000:00:1d.7: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] pci 0000:00:1e.0: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] pci 0000:00:1f.0: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] ata_piix 0000:00:1f.2: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] pci 0000:00:1f.3: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] pci 0000:03:00.0: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] pci 0000:05:01.0: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] yenta_cardbus 0000:05:04.0: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] ohci1394 0000:05:06.0: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] sdhci 0000:05:06.1: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] pci 0000:05:06.2: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] pci 0000:05:06.3: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] pci 0000:05:06.4: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] platform pcspkr: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] serial8250 serial8250: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] i8042 i8042: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] platform eisa.0: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] vesafb vesafb.0: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] platform bluetooth: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] iTCO_wdt iTCO_wdt: EARLY resume
Sep 14 08:44:14 ubuntu kernel: [  407.740000] PM: Finishing wakeup.
Sep 14 08:44:14 ubuntu kernel: [  407.740000] acpi acpi: resuming
Sep 14 08:44:14 ubuntu kernel: [  407.760000] agpgart-intel 0000:00:00.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  407.780000] pci 0000:00:02.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  407.780000] pci 0000:00:02.1: resuming
Sep 14 08:44:14 ubuntu kernel: [  407.780000] HDA Intel 0000:00:1b.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  407.796000] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100106, writing 100102)
Sep 14 08:44:14 ubuntu kernel: [  407.796000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Sep 14 08:44:14 ubuntu kernel: [  408.008000] pcieport-driver 0000:00:1c.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.008000] PM: Writing back config space on device 0000:00:1c.0 at offset 6 (was 0, writing 20200)
Sep 14 08:44:14 ubuntu kernel: [  408.008000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Sep 14 08:44:14 ubuntu kernel: [  408.008000] pcieport-driver 0000:00:1c.1: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.008000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Sep 14 08:44:14 ubuntu kernel: [  408.008000] uhci_hcd 0000:00:1d.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.008000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Sep 14 08:44:14 ubuntu kernel: [  408.008000] uhci_hcd 0000:00:1d.1: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.008000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Sep 14 08:44:14 ubuntu kernel: [  408.008000] uhci_hcd 0000:00:1d.2: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.008000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Sep 14 08:44:14 ubuntu kernel: [  408.008000] uhci_hcd 0000:00:1d.3: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.008000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Sep 14 08:44:14 ubuntu kernel: [  408.008000] ehci_hcd 0000:00:1d.7: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.024000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Sep 14 08:44:14 ubuntu kernel: [  408.024000] pci 0000:00:1e.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.024000] PM: Writing back config space on device 0000:00:1e.0 at offset 9 (was 1fff1, writing 53f15001)
Sep 14 08:44:14 ubuntu kernel: [  408.024000] PM: Writing back config space on device 0000:00:1e.0 at offset 6 (was 20050500, writing 20090500)
Sep 14 08:44:14 ubuntu kernel: [  408.024000] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100004, writing 100007)
Sep 14 08:44:14 ubuntu kernel: [  408.024000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Sep 14 08:44:14 ubuntu kernel: [  408.024000] pci 0000:00:1f.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.024000] ata_piix 0000:00:1f.2: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00005, writing 2b80005)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Sep 14 08:44:14 ubuntu kernel: [  408.040000] pci 0000:00:1f.3: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.040000] pci 0000:03:00.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:03:00.0 at offset f (was 100, writing 10a)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:03:00.0 at offset 4 (was 0, writing d0000000)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:03:00.0 at offset 3 (was 0, writing 10)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100000, writing 100102)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] pci 0000:05:01.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:05:01.0 at offset 3 (was 0, writing 4000)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:05:01.0 at offset 1 (was 2900007, writing 2900003)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] yenta_cardbus 0000:05:04.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:05:04.0 at offset f (was 74001ff, writing 5c001ff)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:05:04.0 at offset e (was 0, writing 28fc)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:05:04.0 at offset d (was 0, writing 2800)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:05:04.0 at offset c (was 0, writing 24fc)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:05:04.0 at offset b (was 0, writing 2400)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:05:04.0 at offset a (was 0, writing 57fff000)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:05:04.0 at offset 9 (was 0, writing 54000000)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:05:04.0 at offset 8 (was 0, writing 53fff000)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:05:04.0 at offset 7 (was 0, writing 50000000)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:05:04.0 at offset 6 (was 20000000, writing b0090605)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:05:04.0 at offset 4 (was 0, writing d0102000)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] PM: Writing back config space on device 0000:05:04.0 at offset 3 (was 24008, writing 2a820)
Sep 14 08:44:14 ubuntu kernel: [  408.040000] ohci1394 0000:05:06.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.056000] PM: Writing back config space on device 0000:05:06.0 at offset 3 (was 800000, writing 804000)
Sep 14 08:44:14 ubuntu kernel: [  408.056000] PM: Writing back config space on device 0000:05:06.0 at offset 1 (was 2100000, writing 2100006)
Sep 14 08:44:14 ubuntu kernel: [  408.112000] sdhci 0000:05:06.1: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.128000] PM: Writing back config space on device 0000:05:06.1 at offset 3 (was 800000, writing 804000)
Sep 14 08:44:14 ubuntu kernel: [  408.128000] PM: Writing back config space on device 0000:05:06.1 at offset 1 (was 2100000, writing 2100006)
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pci 0000:05:06.2: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pci 0000:05:06.3: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pci 0000:05:06.4: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pnp 00:00: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] system 00:01: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pnp 00:02: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pnp 00:03: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pnp 00:04: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pnp 00:05: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] system 00:06: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] system 00:07: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pnp 00:08: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] i8042 kbd 00:09: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] i8042 aux 00:0a: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] platform pcspkr: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pci_express 0000:00:1c.0:pcie00: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pci_express 0000:00:1c.0:pcie02: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pci_express 0000:00:1c.1:pcie00: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] pci_express 0000:00:1c.1:pcie02: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] serial8250 serial8250: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.132000] i8042 i8042: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.164000] atkbd serio0: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.200000] platform eisa.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.200000] serio serio1: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.200000] serio serio2: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.200000] serio serio3: resuming
Sep 14 08:44:14 ubuntu kernel: [  408.200000] psmouse serio4: resuming
Sep 14 08:44:14 ubuntu kernel: [  409.016000] vesafb vesafb.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  409.016000] usb usb2: resuming
Sep 14 08:44:14 ubuntu kernel: [  409.056000] hub 2-0:1.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  409.056000] usb usb3: resuming
Sep 14 08:44:14 ubuntu kernel: [  409.096000] usb usb4: resuming
Sep 14 08:44:14 ubuntu kernel: [  409.136000] usb usb5: resuming
Sep 14 08:44:14 ubuntu kernel: [  409.176000] usb 2-2: resuming
Sep 14 08:44:14 ubuntu kernel: [  409.176000] hci_usb 2-2:1.0: resuming
Sep 14 08:44:14 ubuntu kernel: [  409.176000] hci_usb 2-2:1.1: resuming
Sep 14 08:44:14 ubuntu kernel: [  409.176000] sd 0:0:0:0: resuming
Sep 14 08:44:14 ubuntu kernel: [  409.176000] sr 1:0:0:0: resuming
Sep 14 08:44:14 ubuntu kernel: [  409.176000] platform bluetooth: resuming
Sep 14 08:44:14 ubuntu kernel: [  409.176000] iTCO_wdt iTCO_wdt: resuming
Sep 14 08:44:14 ubuntu kernel: [  409.348000] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
Sep 14 08:44:14 ubuntu kernel: [  409.348000] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000
Sep 14 08:44:14 ubuntu kernel: [  409.352000] APIC error on CPU0: 00(40)
Sep 14 08:44:16 ubuntu kernel: [  411.256000] sda: Mode Sense: 00 3a 00 00
Sep 14 08:44:17 ubuntu kernel: [  412.004000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Sep 14 08:44:17 ubuntu kernel: [  412.008000] ieee80211_crypt: registered algorithm 'NULL'
Sep 14 08:44:17 ubuntu kernel: [  412.020000] PCI: Setting latency timer of device 0000:03:00.0 to 64
Sep 14 08:44:21 ubuntu NetworkManager: <debug info>^I[1189755861.551623] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1b_77_54_29_21'). 
Sep 14 08:44:21 ubuntu NetworkManager: <debug info>^I[1189755861.736802] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Sep 14 08:44:21 ubuntu NetworkManager: <debug info>^I[1189755861.759506] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Sep 14 08:44:21 ubuntu NetworkManager: <debug info>^I[1189755861.759620] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Sep 14 08:44:21 ubuntu NetworkManager: <debug info>^I[1189755861.844806] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Sep 14 08:44:21 ubuntu NetworkManager: <debug info>^I[1189755861.961184] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Sep 14 08:44:22 ubuntu NetworkManager: <debug info>^I[1189755862.069405] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 


```

---

### Post by lincolnlad on 2007-09-19
I found out it was occurring when I passed the vga= option to grub in the menu.lst file.  Removing this solved the problem and now the laptop is waking correctly from suspend and hibernate.

---

