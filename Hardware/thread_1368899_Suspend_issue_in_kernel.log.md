---
title: "Suspend issue in kernel.log"
date: 2009-12-31
forum: Hardware
---

### Post by sarthorks on 2009-12-31
Hello

When i suspend my laptop (either by shutting the lid, or using power button and then the suspend option), and say keep it on suspend for a few minutes, and then wake the system, my kernel logfile shows a little different story.

I suspended the system at 17:23:18, and woke it up at around 17:32:09. From what it appears from this line, 
```

Dec 31 17:32:09 sarthorks kernel: [  390.746223] PM: Preparing system for mem sleep

```
my computer went to sleep only at 17:32??
No wonder 'Back to C!' is also at 17:32, 
```

Dec 31 17:32:09 sarthorks kernel: [    0.811060] Back to C!

```
but shouldn't "preparing system for mem sleep" have appeared at 17:23?

Here is a part of the log file showing the timings for "preparing system for mem sleep" and "back to C!" 
```

Dec 31 17:17:10 sarthorks kernel: [   22.553560] eth0: no IPv6 routers present
Dec 31 17:23:18 sarthorks kernel: [  389.355182] ACPI: PCI interrupt for device 0000:06:00.0 disabled
Dec 31 17:23:19 sarthorks kernel: [  390.746111] Syncing filesystems ... done.
Dec 31 17:32:09 sarthorks kernel: [  390.746223] PM: Preparing system for mem sleep
Dec 31 17:32:09 sarthorks kernel: [  390.746367] Freezing user space processes ... (elapsed 0.00 seconds) done.
Dec 31 17:32:09 sarthorks kernel: [  390.746999] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
Dec 31 17:32:09 sarthorks kernel: [  390.844717] PM: Entering mem sleep
Dec 31 17:32:09 sarthorks kernel: [  390.844720] Suspending console(s)
Dec 31 17:32:09 sarthorks kernel: [  390.858252] ACPI: PCI interrupt for device 0000:00:02.0 disabled
Dec 31 17:32:09 sarthorks kernel: [  390.860227] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Dec 31 17:32:09 sarthorks kernel: [  390.963873] sd 0:0:0:0: [sda] Stopping disk
Dec 31 17:32:09 sarthorks kernel: [  391.945404] ACPI handle has no context!
Dec 31 17:32:09 sarthorks kernel: [  391.945595] ACPI handle has no context!
Dec 31 17:32:09 sarthorks kernel: [  391.945615] ACPI: PCI interrupt for device 0000:08:06.1 disabled
Dec 31 17:32:09 sarthorks kernel: [  391.945622] ACPI handle has no context!
Dec 31 17:32:09 sarthorks kernel: [  391.950744] ACPI handle has no context!
Dec 31 17:32:09 sarthorks kernel: [  391.951454] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [  392.001031] iwl3945: MAC is in deep sleep!
Dec 31 17:32:09 sarthorks kernel: [  392.001054] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [  392.060536] iwl3945: MAC is in deep sleep!
Dec 31 17:32:09 sarthorks kernel: [  392.060549] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [  392.120031] iwl3945: MAC is in deep sleep!
Dec 31 17:32:09 sarthorks kernel: [  392.229444] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [  392.257495] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.257648] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.273295] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.273344] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.273392] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.273997] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.274350] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.274652] ACPI: PCI interrupt for device 0000:00:1a.1 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.274700] ACPI: PCI interrupt for device 0000:00:1a.0 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.285031] Disabling non-boot CPUs ...
Dec 31 17:32:09 sarthorks kernel: [  392.285050] CPU0 attaching NULL sched-domain.
Dec 31 17:32:09 sarthorks kernel: [  392.285052] CPU1 attaching NULL sched-domain.
Dec 31 17:32:09 sarthorks kernel: [  392.398293] CPU 1 is now offline
Dec 31 17:32:09 sarthorks kernel: [  392.398297] SMP alternatives: switching to UP code
Dec 31 17:32:09 sarthorks kernel: [  392.399670] CPU0 attaching sched-domain:
Dec 31 17:32:09 sarthorks kernel: [  392.399673]  domain 0: span 01
Dec 31 17:32:09 sarthorks kernel: [  392.399675]   groups: 01
Dec 31 17:32:09 sarthorks kernel: [  392.399850] CPU1 is down
Dec 31 17:32:09 sarthorks kernel: [    0.811060] Back to C!
Dec 31 17:32:09 sarthorks kernel: [    0.811498] Enabling non-boot CPUs ...

```

uname -r:
```
2.6.24-26-generic
```

Also, all those times when i have kept my laptop on sleep for long durations of time, eg 1 hr, when i wake up the computer, i hear a sudden outburst of fan speed, and then the system powers off suddenly. Is the problem related with these wrong timings somehow?
I will post other relevant information, as asked. 
Help will be appreciated.


Here is the complete log from one command prior to suspend to one after the resume. 

```

Dec 31 17:17:10 sarthorks kernel: [   22.553560] eth0: no IPv6 routers present
Dec 31 17:23:18 sarthorks kernel: [  389.355182] ACPI: PCI interrupt for device 0000:06:00.0 disabled
Dec 31 17:23:19 sarthorks kernel: [  390.746111] Syncing filesystems ... done.
Dec 31 17:32:09 sarthorks kernel: [  390.746223] PM: Preparing system for mem sleep
Dec 31 17:32:09 sarthorks kernel: [  390.746367] Freezing user space processes ... (elapsed 0.00 seconds) done.
Dec 31 17:32:09 sarthorks kernel: [  390.746999] Freezing remaining freezable tasks ... (elapsed 0.09 seconds) done.
Dec 31 17:32:09 sarthorks kernel: [  390.844717] PM: Entering mem sleep
Dec 31 17:32:09 sarthorks kernel: [  390.844720] Suspending console(s)
Dec 31 17:32:09 sarthorks kernel: [  390.858252] ACPI: PCI interrupt for device 0000:00:02.0 disabled
Dec 31 17:32:09 sarthorks kernel: [  390.860227] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Dec 31 17:32:09 sarthorks kernel: [  390.963873] sd 0:0:0:0: [sda] Stopping disk
Dec 31 17:32:09 sarthorks kernel: [  391.945404] ACPI handle has no context!
Dec 31 17:32:09 sarthorks kernel: [  391.945595] ACPI handle has no context!
Dec 31 17:32:09 sarthorks kernel: [  391.945615] ACPI: PCI interrupt for device 0000:08:06.1 disabled
Dec 31 17:32:09 sarthorks kernel: [  391.945622] ACPI handle has no context!
Dec 31 17:32:09 sarthorks kernel: [  391.950744] ACPI handle has no context!
Dec 31 17:32:09 sarthorks kernel: [  391.951454] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [  392.001031] iwl3945: MAC is in deep sleep!
Dec 31 17:32:09 sarthorks kernel: [  392.001054] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [  392.060536] iwl3945: MAC is in deep sleep!
Dec 31 17:32:09 sarthorks kernel: [  392.060549] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [  392.120031] iwl3945: MAC is in deep sleep!
Dec 31 17:32:09 sarthorks kernel: [  392.229444] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [  392.257495] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.257648] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.273295] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.273344] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.273392] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.273997] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.274350] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.274652] ACPI: PCI interrupt for device 0000:00:1a.1 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.274700] ACPI: PCI interrupt for device 0000:00:1a.0 disabled
Dec 31 17:32:09 sarthorks kernel: [  392.285031] Disabling non-boot CPUs ...
Dec 31 17:32:09 sarthorks kernel: [  392.285050] CPU0 attaching NULL sched-domain.
Dec 31 17:32:09 sarthorks kernel: [  392.285052] CPU1 attaching NULL sched-domain.
Dec 31 17:32:09 sarthorks kernel: [  392.398293] CPU 1 is now offline
Dec 31 17:32:09 sarthorks kernel: [  392.398297] SMP alternatives: switching to UP code
Dec 31 17:32:09 sarthorks kernel: [  392.399670] CPU0 attaching sched-domain:
Dec 31 17:32:09 sarthorks kernel: [  392.399673]  domain 0: span 01
Dec 31 17:32:09 sarthorks kernel: [  392.399675]   groups: 01
Dec 31 17:32:09 sarthorks kernel: [  392.399850] CPU1 is down
Dec 31 17:32:09 sarthorks kernel: [    0.811060] Back to C!
Dec 31 17:32:09 sarthorks kernel: [    0.811498] Enabling non-boot CPUs ...
Dec 31 17:32:09 sarthorks kernel: [    0.811564] CPU0 attaching NULL sched-domain.
Dec 31 17:32:09 sarthorks kernel: [    0.821751] SMP alternatives: switching to SMP code
Dec 31 17:32:09 sarthorks kernel: [    0.822889] Booting processor 1/1 eip 3000
Dec 31 17:32:09 sarthorks kernel: [    0.833068] Initializing CPU#1
Dec 31 17:32:09 sarthorks kernel: [    0.913510] Calibrating delay using timer specific routine.. 3324.85 BogoMIPS (lpj=6649706)
Dec 31 17:32:09 sarthorks kernel: [    0.913517] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001 00000000
Dec 31 17:32:09 sarthorks kernel: [    0.913522] monitor/mwait feature present.
Dec 31 17:32:09 sarthorks kernel: [    0.913526] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 31 17:32:09 sarthorks kernel: [    0.913528] CPU: L2 cache: 2048K
Dec 31 17:32:09 sarthorks kernel: [    0.913530] CPU: Physical Processor ID: 0
Dec 31 17:32:09 sarthorks kernel: [    0.913531] CPU: Processor Core ID: 1
Dec 31 17:32:09 sarthorks kernel: [    0.913536] CPU: After all inits, caps: bfebfbff 20000000 00000000 00043940 0000e39d 00000000 00000001 00000000
Dec 31 17:32:09 sarthorks kernel: [    0.914102] CPU1: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz stepping 0d
Dec 31 17:32:09 sarthorks kernel: [    0.914156] CPU0 attaching sched-domain:
Dec 31 17:32:09 sarthorks kernel: [    0.914158]  domain 0: span 03
Dec 31 17:32:09 sarthorks kernel: [    0.914160]   groups: 01 02
Dec 31 17:32:09 sarthorks kernel: [    0.914163] CPU1 attaching sched-domain:
Dec 31 17:32:09 sarthorks kernel: [    0.914164]  domain 0: span 03
Dec 31 17:32:09 sarthorks kernel: [    0.914165]   groups: 02 01
Dec 31 17:32:09 sarthorks kernel: [    0.914504] CPU1 is up
Dec 31 17:32:09 sarthorks kernel: [    0.915254] APIC error on CPU0: 00(40)
Dec 31 17:32:09 sarthorks kernel: [    0.915486] Switched to high resolution mode on CPU 1
Dec 31 17:32:09 sarthorks kernel: [    0.928977] PM: Writing back config space on device 0000:00:02.0 at offset f (was 100, writing 105)
Dec 31 17:32:09 sarthorks kernel: [    0.928991] PM: Writing back config space on device 0000:00:02.0 at offset 1 (was 900007, writing 900003)
Dec 31 17:32:09 sarthorks kernel: [    0.942173] PM: Writing back config space on device 0000:00:02.1 at offset 1 (was 900000, writing 900007)
Dec 31 17:32:09 sarthorks kernel: [    0.942190] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 17
Dec 31 17:32:09 sarthorks kernel: [    0.942197] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.942255] usb usb1: root hub lost power or was reset
Dec 31 17:32:09 sarthorks kernel: [    0.942277] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
Dec 31 17:32:09 sarthorks kernel: [    0.942283] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.942338] usb usb2: root hub lost power or was reset
Dec 31 17:32:09 sarthorks kernel: [    0.943108] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
Dec 31 17:32:09 sarthorks kernel: [    0.943117] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.943441] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100106, writing 100102)
Dec 31 17:32:09 sarthorks kernel: [    0.943474] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
Dec 31 17:32:09 sarthorks kernel: [    0.943484] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.948041] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100007, writing 100407)
Dec 31 17:32:09 sarthorks kernel: [    0.948100] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.948144] PM: Writing back config space on device 0000:00:1c.1 at offset 1 (was 100107, writing 100507)
Dec 31 17:32:09 sarthorks kernel: [    0.948203] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.948247] PM: Writing back config space on device 0000:00:1c.2 at offset 1 (was 100107, writing 100507)
Dec 31 17:32:09 sarthorks kernel: [    0.948305] PCI: Setting latency timer of device 0000:00:1c.2 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.948348] PM: Writing back config space on device 0000:00:1c.3 at offset 1 (was 100107, writing 100507)
Dec 31 17:32:09 sarthorks kernel: [    0.948406] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.948415] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 21
Dec 31 17:32:09 sarthorks kernel: [    0.948425] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.948490] usb usb3: root hub lost power or was reset
Dec 31 17:32:09 sarthorks kernel: [    0.948511] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
Dec 31 17:32:09 sarthorks kernel: [    0.948517] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.948573] usb usb4: root hub lost power or was reset
Dec 31 17:32:09 sarthorks kernel: [    0.948593] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Dec 31 17:32:09 sarthorks kernel: [    0.948598] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.948653] usb usb5: root hub lost power or was reset
Dec 31 17:32:09 sarthorks kernel: [    0.948785] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
Dec 31 17:32:09 sarthorks kernel: [    0.948793] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.948919] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.949022] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2800005, writing 2880005)
Dec 31 17:32:09 sarthorks kernel: [    0.949034] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
Dec 31 17:32:09 sarthorks kernel: [    0.949040] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.950358] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00007, writing 2b00407)
Dec 31 17:32:09 sarthorks kernel: [    0.950420] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Dec 31 17:32:09 sarthorks kernel: [    0.963741] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Dec 31 17:32:09 sarthorks kernel: [    0.963743] ata4.00: ACPI cmd ef/03:42:00:00:00:a0 filtered out
Dec 31 17:32:09 sarthorks kernel: [    0.970223] ata4.00: configured for UDMA/33
Dec 31 17:32:09 sarthorks kernel: [    0.970977] PM: Writing back config space on device 0000:00:1f.3 at offset 4 (was 0, writing 50000000)
Dec 31 17:32:09 sarthorks kernel: [    0.970998] Coming out of suspend...
Dec 31 17:32:09 sarthorks kernel: [    0.972139] PCI: Enabling device 0000:04:00.0 (0000 -> 0002)
Dec 31 17:32:09 sarthorks kernel: [    0.972197] PM: Writing back config space on device 0000:04:00.0 at offset f (was 100, writing 10a)
Dec 31 17:32:09 sarthorks kernel: [    0.972272] PM: Writing back config space on device 0000:04:00.0 at offset 4 (was 0, writing f8000000)
Dec 31 17:32:09 sarthorks kernel: [    0.972287] PM: Writing back config space on device 0000:04:00.0 at offset 3 (was 0, writing 10)
Dec 31 17:32:09 sarthorks kernel: [    0.972309] PM: Writing back config space on device 0000:04:00.0 at offset 1 (was 100002, writing 100506)
Dec 31 17:32:09 sarthorks kernel: [    0.992315] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.002297] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.053429] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.063393] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.073341] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.083357] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.093347] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.103337] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.113329] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.123299] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.133295] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.143283] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.163285] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.173344] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.183331] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.183431] PM: Writing back config space on device 0000:06:00.0 at offset c (was 0, writing f5b20000)
Dec 31 17:32:09 sarthorks kernel: [    1.183484] PM: Writing back config space on device 0000:06:00.0 at offset 3 (was 0, writing 10)
Dec 31 17:32:09 sarthorks kernel: [    1.183501] PM: Writing back config space on device 0000:06:00.0 at offset 1 (was 100000, writing 100102)
Dec 31 17:32:09 sarthorks kernel: [    1.234442] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.244401] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.248317] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fc200000-fc2007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Dec 31 17:32:09 sarthorks kernel: [    1.254500] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.264510] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.264580] ACPI: PCI Interrupt 0000:08:06.1[B] -> GSI 23 (level, low) -> IRQ 21
Dec 31 17:32:09 sarthorks kernel: [    1.264624] PM: Writing back config space on device 0000:08:06.2 at offset 4 (was fc200c00, writing fc201000)
Dec 31 17:32:09 sarthorks kernel: [    1.264633] PM: Writing back config space on device 0000:08:06.2 at offset 1 (was 2100106, writing 2100102)
Dec 31 17:32:09 sarthorks kernel: [    1.264674] PM: Writing back config space on device 0000:08:06.3 at offset 4 (was fc201000, writing fc201400)
Dec 31 17:32:09 sarthorks kernel: [    1.264703] PM: Writing back config space on device 0000:08:06.4 at offset f (was 20b, writing 2ff)
Dec 31 17:32:09 sarthorks kernel: [    1.264726] PM: Writing back config space on device 0000:08:06.4 at offset 4 (was fc201400, writing ffffff00)
Dec 31 17:32:09 sarthorks kernel: [    1.264735] PM: Writing back config space on device 0000:08:06.4 at offset 1 (was 2100102, writing 2100542)
Dec 31 17:32:09 sarthorks kernel: [    1.274480] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.284473] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.284485] ata2: SATA link down (SStatus 0 SControl 300)
Dec 31 17:32:09 sarthorks kernel: [    1.284501] ata3: SATA link down (SStatus 0 SControl 300)
Dec 31 17:32:09 sarthorks kernel: [    1.294467] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.304442] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.314437] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.324435] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.355452] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.365451] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.375641] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.389964] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.399984] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.419885] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.439785] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.467016] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Dec 31 17:32:09 sarthorks kernel: [    1.658705] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 31 17:32:09 sarthorks kernel: [    1.659745] ata1.00: _GTF unexpected object type 0x1
Dec 31 17:32:09 sarthorks kernel: [    1.660877] ata1.00: configured for UDMA/100
Dec 31 17:32:09 sarthorks kernel: [    1.662880] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 31 17:32:09 sarthorks kernel: [    1.662932] sd 0:0:0:0: [sda] Write Protect is off
Dec 31 17:32:09 sarthorks kernel: [    1.662936] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 31 17:32:09 sarthorks kernel: [    1.663022] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 31 17:32:09 sarthorks kernel: [    1.808254] sd 0:0:0:0: [sda] Starting disk
Dec 31 17:32:09 sarthorks kernel: [    1.831376] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
Dec 31 17:32:09 sarthorks kernel: [    1.832863] PM: Finishing wakeup.
Dec 31 17:32:09 sarthorks kernel: [    1.832865] Restarting tasks ... <6>usb 2-1: USB disconnect, address 8
Dec 31 17:32:09 sarthorks kernel: [    1.850099] done.
Dec 31 17:32:09 sarthorks kernel: [    2.199686] usb 6-4: USB disconnect, address 11
Dec 31 17:32:09 sarthorks kernel: [    2.311492] usb 6-4: new high speed USB device using ehci_hcd and address 13
Dec 31 17:32:09 sarthorks kernel: [    2.394824] tg3.c:v3.86 (November 9, 2007)
Dec 31 17:32:09 sarthorks kernel: [    2.394881] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 19
Dec 31 17:32:09 sarthorks kernel: [    2.394902] PCI: Setting latency timer of device 0000:06:00.0 to 64
Dec 31 17:32:09 sarthorks kernel: [    2.455574] usb 6-4: configuration #1 chosen from 1 choice
Dec 31 17:32:09 sarthorks kernel: [    2.455859] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b013)
Dec 31 17:32:09 sarthorks kernel: [    2.693901] usb 2-1: new full speed USB device using uhci_hcd and address 9
Dec 31 17:32:09 sarthorks kernel: [    2.703385] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:1e:ec:09:c2:12
Dec 31 17:32:09 sarthorks kernel: [    2.703393] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
Dec 31 17:32:09 sarthorks kernel: [    2.703396] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Dec 31 17:32:09 sarthorks kernel: [    2.775006] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 31 17:32:09 sarthorks kernel: [    2.857016] usb 2-1: configuration #1 chosen from 1 choice
Dec 31 17:32:09 sarthorks kernel: [    2.975952] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 31 17:32:11 sarthorks kernel: [    4.563547] tg3: eth0: Link is up at 100 Mbps, full duplex.
Dec 31 17:32:11 sarthorks kernel: [    4.563552] tg3: eth0: Flow control is on for TX and on for RX.
Dec 31 17:32:11 sarthorks kernel: [    4.565621] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 31 17:32:21 sarthorks kernel: [   14.603987] eth0: no IPv6 routers present

```

---

### Post by sarthorks on 2009-12-31
Bump.

---

### Post by GeorgeVita on 2009-12-31
Hi **sarthorks**, I am trying to simulate your case to my netbook but I saw your kernel is very old!

What Ubuntu version are you using? Can you update it?

>>> Ubuntu 9.04 (i386) now uses kernel: 2.6.28-17-generic #58


**EDIT: I just tested, and seems like yours! Log file is updated 'at resume time!'  bug?** 

Regards,
George

---

### Post by sarthorks on 2009-12-31
> **GeorgeVita said:**
> Hi **sarthorks**, I am trying to simulate your case to my netbook but I saw your kernel is very old!

What Ubuntu version are you using? Can you update it?

>>> Ubuntu 9.04 (i386) now uses kernel: 2.6.28-17-generic #58


**EDIT: I just tested, and seems like yours! Log file is updated 'at resume time!'  bug?** 

Regards,
George
I'm using Hardy.
I wanted to wait till 10.04 got out before doing a clean install.

Cant i update my kernel further in hardy itself?
And are you saying you dont have a similar issue in your kernel? 
And can you tell me when EXACTLY is the "prepering system for mem sleep" supposed to appear? At suspend? or at resume?

---

### Post by sarthorks on 2009-12-31
> **GeorgeVita said:**
> 

**EDIT: I just tested, and seems like yours! Log file is updated 'at resume time!'  bug?** 


What exactly do you mean by that?

---

### Post by GeorgeVita on 2009-12-31
This behaviour exists also in newer releases, till the Ubuntu 10.04 (now in development)!

I am running LL a1+updates with kernel: 2.6.32-9-generic #13
and suspends in the same way!
```
Dec 31 15:08:27 LL23dec kernel: [   23.005659] type=1505 audit(1262264907.747:10):  operation="profile_load" pid=1098 name="/usr/bin/evince-previewer"
Dec 31 15:08:27 LL23dec kernel: [   23.032179] type=1505 audit(1262264907.771:11):  operation="profile_load" pid=1098 name="/usr/bin/evince-thumbnailer"
Dec 31 15:08:27 LL23dec kernel: [   23.122392] Skipping EDID probe due to cached edid
Dec 31 15:08:27 LL23dec kernel: [   23.161150] Skipping EDID probe due to cached edid
Dec 31 15:08:28 LL23dec kernel: [   23.542728] ppdev: user-space parallel port driver
Dec 31 15:08:29 LL23dec kernel: [   24.909253] Skipping EDID probe due to cached edid
Dec 31 15:08:29 LL23dec kernel: [   24.950085] Skipping EDID probe due to cached edid
Dec 31 15:08:29 LL23dec kernel: [   24.989327] Skipping EDID probe due to cached edid
Dec 31 15:08:36 LL23dec kernel: [   32.252050] wlan0: no IPv6 routers present
Dec 31 15:10:02 LL23dec kernel: [  117.270553] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 112
Dec 31 15:10:05 LL23dec kernel: [  120.810029] Skipping EDID probe due to cached edid
Dec 31 15:10:05 LL23dec kernel: [  120.854406] Skipping EDID probe due to cached edid
Dec 31 15:10:05 LL23dec kernel: [  120.909815] Skipping EDID probe due to cached edid
Dec 31 15:10:06 LL23dec kernel: [  122.249213] Skipping EDID probe due to cached edid
Dec 31 15:10:08 LL23dec kernel: [  123.493227] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
Dec 31 15:13:23 LL23dec kernel: [  168.412457] PM: Syncing filesystems ... done.
Dec 31 15:13:23 LL23dec kernel: [  168.448080] PM: Preparing system for mem sleep
Dec 31 15:13:23 LL23dec kernel: [  168.448094] Freezing user space processes ... (elapsed 0.00 seconds) done.
Dec 31 15:13:23 LL23dec kernel: [  168.449751] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Dec 31 15:13:23 LL23dec kernel: [  168.450018] PM: Entering mem sleep
Dec 31 15:13:23 LL23dec kernel: [  168.450042] Suspending console(s) (use no_console_suspend to debug)
Dec 31 15:13:23 LL23dec kernel: [  168.451489] btusb_intr_complete: hci0 urb f318c400 failed to resubmit (1)
Dec 31 15:13:23 LL23dec kernel: [  168.452473] btusb_bulk_complete: hci0 urb f318c100 failed to resubmit (1)
Dec 31 15:13:23 LL23dec kernel: [  168.453473] btusb_bulk_complete: hci0 urb f318c180 failed to resubmit (1)
Dec 31 15:13:23 LL23dec kernel: [  168.500091] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Dec 31 15:13:23 LL23dec kernel: [  168.500538] sd 0:0:0:0: [sda] Stopping disk
Dec 31 15:13:23 LL23dec kernel: [  169.343115] ACPI handle has no context!
Dec 31 15:13:23 LL23dec kernel: [  169.343208] rt2860 0000:01:00.0: PCI INT A disabled
Dec 31 15:13:23 LL23dec kernel: [  169.343218] ACPI handle has no context!
Dec 31 15:13:23 LL23dec kernel: [  169.356222] ACPI handle has no context!
Dec 31 15:13:23 LL23dec kernel: [  169.356241] ATL1E 0000:03:00.0: PCI INT A disabled
Dec 31 15:13:23 LL23dec kernel: [  169.356255] ACPI handle has no context!
Dec 31 15:13:23 LL23dec kernel: [  169.372312] ata_piix 0000:00:1f.2: PCI INT B disabled
Dec 31 15:13:23 LL23dec kernel: [  169.388096] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Dec 31 15:13:23 LL23dec kernel: [  169.388119] uhci_hcd 0000:00:1d.3: PCI INT D disabled
Dec 31 15:13:23 LL23dec kernel: [  169.388138] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Dec 31 15:13:23 LL23dec kernel: [  169.388158] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Dec 31 15:13:23 LL23dec kernel: [  169.388177] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Dec 31 15:13:23 LL23dec kernel: [  169.388234] HDA Intel 0000:00:1b.0: PCI INT A disabled
Dec 31 15:13:23 LL23dec kernel: [  169.424725] i915 0000:00:02.0: PCI INT A disabled
Dec 31 15:13:23 LL23dec kernel: [  169.440188] PM: suspend devices took 0.992 seconds
Dec 31 15:13:23 LL23dec kernel: [  169.456301] ACPI: Preparing to enter system sleep state S3
Dec 31 15:13:23 LL23dec kernel: [  169.485230] Disabling non-boot CPUs ...
Dec 31 15:13:23 LL23dec kernel: [  169.588034] CPU 1 is now offline
Dec 31 15:13:23 LL23dec kernel: [  169.588040] SMP alternatives: switching to UP code
Dec 31 15:13:23 LL23dec kernel: [  169.593511] CPU0 attaching NULL sched-domain.
Dec 31 15:13:23 LL23dec kernel: [  169.593519] CPU1 attaching NULL sched-domain.
Dec 31 15:13:23 LL23dec kernel: [  169.593533] CPU0 attaching NULL sched-domain.
Dec 31 15:13:23 LL23dec kernel: [  169.594157] CPU1 is down
Dec 31 15:13:23 LL23dec kernel: [  169.594179] Back to C!
Dec 31 15:13:23 LL23dec kernel: [  169.594179] CPU0: Thermal LVT vector (0xfa) already installed
Dec 31 15:13:23 LL23dec kernel: [  169.594179] Enabling non-boot CPUs ...
Dec 31 15:13:23 LL23dec kernel: [  169.594179] SMP alternatives: switching to SMP code
Dec 31 15:13:23 LL23dec kernel: [  169.599607] Booting processor 1 APIC 0x1 ip 0x6000
Dec 31 15:13:23 LL23dec kernel: [  169.593243] Initializing CPU#1
Dec 31 15:13:23 LL23dec kernel: [  169.593243] Calibrating delay using timer specific routine.. 3191.99 BogoMIPS (lpj=6383996)
Dec 31 15:13:23 LL23dec kernel: [  169.593243] CPU: L1 I cache: 32K, L1 D cache: 24K
Dec 31 15:13:23 LL23dec kernel: [  169.593243] CPU: L2 cache: 512K
Dec 31 15:13:23 LL23dec kernel: [  169.593243] CPU: Physical Processor ID: 0
Dec 31 15:13:23 LL23dec kernel: [  169.593243] CPU: Processor Core ID: 0
Dec 31 15:13:23 LL23dec kernel: [  169.593243] CPU1: Thermal monitoring enabled (TM2)
Dec 31 15:13:23 LL23dec kernel: [  169.688156] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
Dec 31 15:13:23 LL23dec kernel: [  169.688269] CPU0 attaching NULL sched-domain.
Dec 31 15:13:23 LL23dec kernel: [  169.700040] CPU0 attaching sched-domain:
Dec 31 15:13:23 LL23dec kernel: [  169.700049]  domain 0: span 0-1 level SIBLING
Dec 31 15:13:23 LL23dec kernel: [  169.700056]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
Dec 31 15:13:23 LL23dec kernel: [  169.700071]   domain 1: span 0-1 level MC
Dec 31 15:13:23 LL23dec kernel: [  169.700077]    groups: 0-1 (cpu_power = 1178)
Dec 31 15:13:23 LL23dec kernel: [  169.700089] CPU1 attaching sched-domain:
Dec 31 15:13:23 LL23dec kernel: [  169.700095]  domain 0: span 0-1 level SIBLING
Dec 31 15:13:23 LL23dec kernel: [  169.700101]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
Dec 31 15:13:23 LL23dec kernel: [  169.700115]   domain 1: span 0-1 level MC
Dec 31 15:13:23 LL23dec kernel: [  169.700121]    groups: 0-1 (cpu_power = 1178)
Dec 31 15:13:23 LL23dec kernel: [  169.704040] CPU1 is up
Dec 31 15:13:23 LL23dec kernel: [  169.704226] ACPI: Waking up from system sleep state S3
Dec 31 15:13:23 LL23dec kernel: [  169.772519] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
Dec 31 15:13:23 LL23dec kernel: [  169.772580] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x1fff1, writing 0x80318021)
Dec 31 15:13:23 LL23dec kernel: [  169.772593] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0xfff0, writing 0x80108000)
Dec 31 15:13:23 LL23dec kernel: [  169.772606] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0xf0, writing 0x1010)
Dec 31 15:13:23 LL23dec kernel: [  169.772627] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100104, writing 0x100507)
Dec 31 15:13:23 LL23dec kernel: [  169.772708] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x1fff1, writing 0x80518041)
Dec 31 15:13:23 LL23dec kernel: [  169.772733] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100107, writing 0x100507)
Dec 31 15:13:23 LL23dec kernel: [  169.772815] pcieport 0000:00:1c.3: restoring config space at offset 0x7 (was 0xf0, writing 0x2020)
Dec 31 15:13:23 LL23dec kernel: [  169.772837] pcieport 0000:00:1c.3: restoring config space at offset 0x1 (was 0x100106, writing 0x100507)
Dec 31 15:13:23 LL23dec kernel: [  169.772917] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Dec 31 15:13:23 LL23dec kernel: [  169.772966] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Dec 31 15:13:23 LL23dec kernel: [  169.773018] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Dec 31 15:13:23 LL23dec kernel: [  169.773067] uhci_hcd 0000:00:1d.3: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
Dec 31 15:13:23 LL23dec kernel: [  169.773125] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
Dec 31 15:13:23 LL23dec kernel: [  169.773411] rt2860 0000:01:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
Dec 31 15:13:23 LL23dec kernel: [  169.773448] rt2860 0000:01:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xfbef0000)
Dec 31 15:13:23 LL23dec kernel: [  169.773461] rt2860 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x8)
Dec 31 15:13:23 LL23dec kernel: [  169.773477] rt2860 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Dec 31 15:13:23 LL23dec kernel: [  169.944356] PM: Device PNP0C0D:00 failed to resume: error 1
Dec 31 15:13:23 LL23dec kernel: [  169.953494] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 31 15:13:23 LL23dec kernel: [  169.953504] i915 0000:00:02.0: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.074205] [drm] LVDS-8: set mode 1024x600 e
Dec 31 15:13:23 LL23dec kernel: [  170.114197] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 31 15:13:23 LL23dec kernel: [  170.114209] HDA Intel 0000:00:1b.0: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.114248] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 31 15:13:23 LL23dec kernel: [  170.114259] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.114289] usb usb2: root hub lost power or was reset
Dec 31 15:13:23 LL23dec kernel: [  170.114315] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 31 15:13:23 LL23dec kernel: [  170.114326] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.114354] usb usb3: root hub lost power or was reset
Dec 31 15:13:23 LL23dec kernel: [  170.114378] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 31 15:13:23 LL23dec kernel: [  170.114388] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.114416] usb usb4: root hub lost power or was reset
Dec 31 15:13:23 LL23dec kernel: [  170.114440] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Dec 31 15:13:23 LL23dec kernel: [  170.114450] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.114477] usb usb5: root hub lost power or was reset
Dec 31 15:13:23 LL23dec kernel: [  170.114522] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Dec 31 15:13:23 LL23dec kernel: [  170.114533] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.114568] pci 0000:00:1e.0: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.114584] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Dec 31 15:13:23 LL23dec kernel: [  170.114593] ata_piix 0000:00:1f.2: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.117094] ATL1E 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 31 15:13:23 LL23dec kernel: [  170.117108] ATL1E 0000:03:00.0: setting latency timer to 64
Dec 31 15:13:23 LL23dec kernel: [  170.125101] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec 31 15:13:23 LL23dec kernel: [  170.504474] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
Dec 31 15:13:23 LL23dec kernel: [  170.504484] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
Dec 31 15:13:23 LL23dec kernel: [  170.504869] ata1.00: ACPI cmd c6/00:10:00:00:00:a0 (SET MULTIPLE MODE) succeeded
Dec 31 15:13:23 LL23dec kernel: [  170.528978] ata1.00: configured for UDMA/133
Dec 31 15:13:23 LL23dec kernel: [  170.552942] ata1.00: configured for UDMA/133
Dec 31 15:13:23 LL23dec kernel: [  170.552955] ata1: EH complete
Dec 31 15:13:23 LL23dec kernel: [  170.630679] sd 0:0:0:0: [sda] Starting disk
Dec 31 15:13:23 LL23dec kernel: [  170.792084] usb 1-5: reset high speed USB device using ehci_hcd and address 3
Dec 31 15:13:23 LL23dec kernel: [  171.036082] usb 1-8: reset high speed USB device using ehci_hcd and address 5
Dec 31 15:13:23 LL23dec kernel: [  171.332082] usb 5-1: reset full speed USB device using uhci_hcd and address 2
Dec 31 15:13:23 LL23dec kernel: [  172.051138] btusb 5-1:1.0: no reset_resume for driver btusb?
Dec 31 15:13:23 LL23dec kernel: [  172.051149] btusb 5-1:1.1: no reset_resume for driver btusb?
Dec 31 15:13:23 LL23dec kernel: [  172.300850] PM: resume devices took 2.528 seconds
Dec 31 15:13:23 LL23dec kernel: [  172.300914] PM: Finishing wakeup.
Dec 31 15:13:23 LL23dec kernel: [  172.300918] Restarting tasks ... done.
Dec 31 15:13:23 LL23dec kernel: [  172.709855] ATL1E 0000:03:00.0: irq 27 for MSI/MSI-X
Dec 31 15:13:23 LL23dec kernel: [  172.738816] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 31 15:13:23 LL23dec kernel: [  172.754136] RX DESC f2761000  size = 2048
Dec 31 15:13:23 LL23dec kernel: [  172.754587] <-- RTMPAllocTxRxRingMemory, Status=0
Dec 31 15:13:23 LL23dec kernel: [  172.758287] --> Error 2 opening /etc/Wireless/RT2860STA/RT2860STA.dat
Dec 31 15:13:23 LL23dec kernel: [  172.758298] 1. Phy Mode = 0
Dec 31 15:13:23 LL23dec kernel: [  172.758303] 2. Phy Mode = 0
Dec 31 15:13:23 LL23dec kernel: [  172.785156] 3. Phy Mode = 0
Dec 31 15:13:23 LL23dec kernel: [  172.807911] MCS Set = 00 00 00 00 00

``` In above example 'resume' done 15:13

EDIT: just created a [thread]("http://ubuntuforums.org/showthread.php?t=1369020") for testing by others involved in development/test of LL


G

---

### Post by sarthorks on 2009-12-31
I see. 
It will hopefully turn out to be a kernel logging bug.
If its ALWAYS been logging like this, and considering suspend HAS conserved power for all of us, it shouldn't be an issue with the suspend itself, but only the logging.

---

### Post by GeorgeVita on 2009-12-31
I think you are right. Possibly some events are buffered, then suspends and after resume comes the 'logger' to make the new/last entries!

Regards and Happy new Year (after 4 hours here!)
George

---

