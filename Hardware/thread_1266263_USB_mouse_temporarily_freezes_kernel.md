---
title: "USB mouse temporarily freezes kernel"
date: 2009-09-14
forum: Hardware
---

### Post by ManDay on 2009-09-14
The following problem emerged from my research on slow hibernation/resume as in [this thread]("http://ubuntuforums.org/showthread.php?t=1064894").

The affected computer is an...

[B]EEE PC 1000H, no additional peripheral devices, a very freshly installated instance of Ubuntu with only a few, hand-picked packages out of a minimal install

[U][SIZE=5]Phenomenology:[/SIZE]

[/U][/B]Resuming from hibernation (aka Suspend-to-disk) with the USB mouse being plugged in it takes (according to the progress displayed by *uswsusp*) only a few seconds to load the memory from swap. Afterwards, however, the kernel remains stuck in a black screen without any output before eventually the desktop comes up after approximately 30 seconds.

This only happens when resuming from hibernation. A normal boot is not affected by a mouse being plugged in in any kind of way.

Removing the mouse before resume, the desktop returns immediately after *uswsusp* claims to have finished loading the memory (which takes approx. 5 seconds).

[SIZE=5]_**Logs:**_[SIZE=2][SIZE=1]
[/SIZE][/SIZE][/SIZE]
I'll try to provide you with the necessary information the best I can. The following logs I reckon will render useful for determining the cause of the problem (click the text):


[LIST=1]
[*][Normal boot, without mouse plugged in]("http://manday.pastebin.com/f571dee68")
[*][Normal boot, with mouse plugged in]("http://manday.pastebin.com/f7f88ff35")
[*][Resume, without mouse plugged in]("http://manday.pastebin.com/m7d75d179")
[*][Resume, with mouse plugged in]("http://manday.pastebin.com/m1b0c7058")
[*][Plugging in the mouse]("http://manday.pastebin.com/m2ff45c34")
[*][*/var/log/pm-suspend.log*]("http://manday.pastebin.com/m361be49e"), without mouse plugged in
[*][*/var/log/pm-suspend.log*]("http://manday.pastebin.com/m289fda5d"), with mouse plugged in
[/LIST]
Aditionally, I'll quote the according snippets which are most important to my understanding, to give you a better overview:

```
[B]Resume, without mouse
[/B]
[  253.526742] uvcvideo: Failed to query (1) UVC control 2 (unit 0) : -71 (exp. 26).
[  253.526760] uvcvideo 1-8:1.1: resume error -5
[  254.628624] pci 0000:00:02.0: setting latency timer to 64
[  254.633987] uvcvideo: Failed to query (1) UVC control 2 (unit 0) : -71 (exp. 26).
[  254.634004] uvcvideo 1-8:1.1: resume error -5
[  254.687593] Restarting tasks ... done.
[  254.840573] PM: Basic memory bitmaps freed
[COLOR=red][  254.913061] usb 1-5: reset high speed USB device using ehci_hcd and address 3[/COLOR]
[  256.040646] ATL1E 0000:03:00.0: irq 2300 for MSI/MSI-X
[  256.064558] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  256.076342] RX DESC f2413000  size = 2048
[  256.076937] <-- RTMPAllocTxRxRingMemory, Status=0
[  256.082337] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[  256.082348] 1. Phy Mode = 0
[  256.082353] 2. Phy Mode = 0
[  256.110124] 3. Phy Mode = 0
[  256.135048] MCS Set = 00 00 00 00 00
[  256.136699] <==== RTMPInitialize, Status=0
``````
**Resume with mouse**

[  111.216882] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[  111.216892] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[  111.216997] pci 0000:00:1e.0: setting latency timer to 64
[  111.217087] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b80001, writing 0x2b80005)
[  111.217107] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  111.217115] ata_piix 0000:00:1f.2: setting latency timer to 64
[  111.236288] ATL1E 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  111.236306] ATL1E 0000:03:00.0: setting latency timer to 64
[  111.260277] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  111.260445] sd 0:0:0:0: [sda] Starting disk
[  111.384591] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[  111.384598] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[  111.384739] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded
[  111.408634] ata1.00: configured for UDMA/133
[  111.432630] ata1.00: configured for UDMA/133
[  111.432640] ata1: EH complete
[  111.444347] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[  111.444441] sd 0:0:0:0: [sda] Write Protect is off
[  111.444451] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  111.444571] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  111.444647] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[  111.444688] sd 0:0:0:0: [sda] Write Protect is off
[  111.444693] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  111.444760] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  111.500140] Clocksource tsc unstable (delta = -390405436 ns)
[  112.712495] pci 0000:00:02.0: setting latency timer to 64
[  112.766788] Restarting tasks ... done.
[  112.903305] PM: Basic memory bitmaps freed
[COLOR=red][  143.928127] usb 1-5: reset high speed USB device using ehci_hcd and address 3[/COLOR]
[  145.504991] ATL1E 0000:03:00.0: irq 2300 for MSI/MSI-X
[  145.531908] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  145.542539] RX DESC f50a6000  size = 2048
[  145.543064] <-- RTMPAllocTxRxRingMemory, Status=0
[  145.547568] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
[  145.547579] 1. Phy Mode = 0
[  145.547584] 2. Phy Mode = 0
[  145.576835] 3. Phy Mode = 0
[  145.599659] MCS Set = 00 00 00 00 00
[  145.601296] <==== RTMPInitialize, Status=0
``````
**Plugging in the mouse**

[  414.416139] usb 2-2: new low speed USB device using uhci_hcd and address 3
[  414.591363] usb 2-2: configuration #1 chosen from 1 choice
[  414.623225] input: Genius 4D Scroll Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input12
[  414.657921] generic-usb 0003:0458:0056.0002: input,hidraw0: USB HID v1.10 Mouse [Genius 4D Scroll Mouse] on usb-0000:00:1d.0-2/input0
```If you need any information besides the above, please let me know and I'll gladly tell you. Thank you for your help.

---

### Post by ManDay on 2009-09-15
Somtimes it even takes a long time without the mouse plugged in. However, it's still between **PM: Basic memory bitmaps freed** and **usb 1-5: reset high speed USB device using ehci_hcd and address 2**.

---

