---
title: "&quot;very bad!&quot; - host controller halted"
date: 2008-12-24
forum: Hardware
---

### Post by kuloch on 2008-12-24
I noticed this popping up while booting, and the "very bad" naturally caught my eye.  It happens 3 times, and I suspect it has to do with my recent suspend breakage.  Perhaps both came with one of the recent updates?
```
[   78.844328] uhci_hcd 0000:00:1d.2: host controller process error, something bad happened!
[   78.844385] uhci_hcd 0000:00:1d.2: host controller halted, very bad!
[   78.844444] uhci_hcd 0000:00:1d.2: HC died; cleaning up
```([full dmesg output]("http://iv.gotdns.org/misc/dmesg.2008-12-23.txt"))

I expect that's referring to the USB host controller, although it could be the southbridge for all I know.  Some searching indicates this occurring with a wide variety of issues (usually at install or when plugging in a USB device).  But I have no devices plugged in.  Although it seems that plugging a flash drive in gives oddly intermittent results.  It pulls up the contents just fine, but it seems to unmount it several seconds later - or maybe it's just when I try accessing it.  And one of the ports isn't doing anything.

The other - probably related - issue is a seemingly-intermittent failure to suspend.  The other day, I couldn't get it to suspend at all, so I searched around and found suggestions to use the "noapic" boot flag (along with a host of other suggestions, but only that one didn't screw things up).  I thought it was helping until I booted again without it to find that I could suspend fine.  Then, the next day, it failed to suspend.  Tonight, after a clean boot, it suspended 3 times successfully before failing, but now it refuses to suspend (also 3 times).  Here are the things that jump out to me from another dmesg:
```
[   13.304209] atkbd.c: Spurious NAK on isa0060/serio0. Some program might be trying access hardware directly.
...
[   17.619045] ACPI: PCI interrupt for device 0000:00:02.0 disabled
[   17.619172] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[   17.619284] sd 0:0:0:0: [sda] Stopping disk
[   17.621793] ACPI handle has no context!
[   17.621813] ACPI: PCI interrupt for device 0000:06:06.4 disabled
[   17.621819] ACPI handle has no context!
...
[   17.622661] pci_device_suspend(): usb_hcd_pci_suspend+0x0/0x170 [usbcore]() returns -16
[   17.622700] suspend_device(): pci_device_suspend+0x0/0x60() returns -16
[   17.622709] Could not suspend device 0000:00:1d.3: error -16
[   17.622772] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[   17.622777] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   17.622785] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   17.622797] PM: Writing back config space on device 0000:00:1d.7 at offset f (was 100, writing 10b)
```([full dmesg output]("http://iv.gotdns.org/misc/dmesg.2008-12-24.txt"))

Any thoughts on where I should look?  Any more output that might be helpful?

---

