---
title: "Acer Travelmate 2420 Hibernation Problems"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by muadib on 2006-10-17
Hi, I'm wondering if anyone has gotten this laptop to suspend ? Any help would be greatly appreciated. I have an activated swap partition and this partition is greater in size than the amount of ram that I have. Thanks, Mathieu

This is the relevant info in dmesg that comes up after I try : 
# echo -n disk > /sys/power/state


[ 1315.449000] Freezing cpus ...
[ 1315.449000] Stopping tasks: ==============================================================================================================|
[ 1315.464000] Shrinking memory...  -\done (13288 pages freed)
[ 1315.608000] ACPI: PCI interrupt for device 0000:06:09.0 disabled
[ 1315.608000] eth0: Going into suspend...
[ 1315.611000] ACPI: PCI interrupt for device 0000:06:05.0 disabled
[ 1315.627000] ACPI: PCI interrupt for device 0000:00:1e.2 disabled
[ 1315.627000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[ 1315.638000] Device `[USB7]' is not power manageable<6>ACPI: PCI interrupt for device 0000:00:1d.3 disabled
[ 1315.638000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[ 1315.638000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[ 1315.638000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[ 1315.638000] 
[ 1315.638000] swsusp: Need to copy 89914 pages
[ 1315.638000] swsusp: critical section/: done (89914 pages copied)
[ 1315.638000] swsusp: Restoring Highmem
[ 1318.681000] PCI: Enabling device 0000:00:1d.0 (0000 -> 0001)
[ 1318.681000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 193
[ 1318.681000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[ 1318.681000] PCI: Enabling device 0000:00:1d.1 (0000 -> 0001)
[ 1318.681000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 201
[ 1318.681000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[ 1318.681000] PCI: Enabling device 0000:00:1d.2 (0000 -> 0001)
[ 1318.682000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 209
[ 1318.682000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[ 1318.682000] PCI: Enabling device 0000:00:1d.3 (0000 -> 0001)
[ 1318.682000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 217
[ 1318.682000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[ 1318.693000] Device `[USB7]' is not power manageablePCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[ 1318.693000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 193
[ 1318.693000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[ 1318.693000] PM: Writing back config space on device 0000:00:1d.7 at offset f (was 100, writing 10b)
[ 1318.693000] PM: Writing back config space on device 0000:00:1d.7 at offset 4 (was 0, writing b0040000)
[ 1318.693000] PM: Writing back config space on device 0000:00:1d.7 at offset 1 (was 2900006, writing 2900106)
[ 1318.693000] usb usb5: root hub lost power or was reset
[ 1318.697000] ehci_hcd 0000:00:1d.7: debug port 1
[ 1318.697000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[ 1318.701000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 1318.701000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[ 1318.701000] PCI: Enabling device 0000:00:1e.2 (0000 -> 0003)
[ 1318.701000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 21 (level, low) -> IRQ 177
[ 1318.701000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[ 1318.954000] eth0: Coming out of suspend...
[ 1318.965000] PCI: Enabling device 0000:06:05.0 (0000 -> 0002)
[ 1318.965000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 21 (level, low) -> IRQ 177
[ 1318.965000] PM: Writing back config space on device 0000:06:05.0 at offset f (was 18030100, writing 1803010a)
[ 1318.965000] PM: Writing back config space on device 0000:06:05.0 at offset 4 (was 0, writing b0100000)
[ 1318.965000] PM: Writing back config space on device 0000:06:05.0 at offset 3 (was 0, writing 2008)
[ 1318.965000] PM: Writing back config space on device 0000:06:05.0 at offset 1 (was 2900002, writing 2900106)
[ 1318.965000] PM: Writing back config space on device 0000:06:09.0 at offset 1 (was 2100000, writing 2100007)
[ 1318.965000] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 22 (level, low) -> IRQ 169
[ 1319.089000] pnp: Device 00:06 does not support activation.
[ 1319.089000] pnp: Device 00:07 does not support activation.
[ 1319.755000] swsusp: Cannot find swap device, try swapon -a.
[ 1319.797000] Restarting tasks... done
[ 1319.861000] Thawing cpus ...
[ 1350.687000] atkbd.c: Unknown key pressed (translated set 2, code 0xb3 on isa0060/serio0).
[ 1350.687000] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.
[ 1350.808000] atkbd.c: Unknown key released (translated set 2, code 0xb3 on isa0060/serio0).
[ 1350.808000] atkbd.c: Use 'setkeycodes e033 <keycode>' to make it known.

---

### Post by muadib on 2006-10-20
Turns out that there is nothing wrong with hibernation with this laptop, it was just a question of configuring the swap properly.

I am happy to report that I have power management, wifi, sound and accelerated graphics working well on this laptop.

Mathieu

---

### Post by benhall on 2006-10-21
What did you do to configure the swap properly? After hibernation, my swap is frequently corrupted and needs reformating. It worked without issue in dapper.

Thanks

---

