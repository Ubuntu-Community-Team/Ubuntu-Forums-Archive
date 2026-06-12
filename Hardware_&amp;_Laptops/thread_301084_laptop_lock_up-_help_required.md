---
title: "laptop lock up- help required"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by lir on 2006-11-16
Hey everyone,

I've started experiencing these weird freezes and lockups that happen almost continously every several minutes for 2-4 seconds each time.

It has gotten worse and freezed up the entire system, the logfiles show:
/var/log/syslog:

Nov 17 00:38:20 localhost kernel: [17197168.972000] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 5 bytes away.
Nov 17 00:39:13 localhost kernel: [17197220.344000] ata2: dev 0: ATAPI check failed
Nov 17 00:39:13 localhost kernel: [17197220.344000] ata2: PIO error
Nov 17 00:39:13 localhost kernel: [17197220.344000] ata2: translated ATA stat/err 0x59/40 to SCSI SK/ASC/ASCQ 0x3/11/04
Nov 17 00:39:24 localhost kernel: [17197232.812000] BUG: soft lockup detected on CPU#0!
Nov 17 00:39:24 localhost kernel: [17197232.812000]
Nov 17 00:39:24 localhost kernel: [17197232.812000] Pid: 0, comm:              swapper
Nov 17 00:39:24 localhost kernel: [17197232.812000] EIP: 0060:[handle_IRQ_event+24/112] CPU: 0
Nov 17 00:39:24 localhost kernel: [17197232.812000] EIP is at handle_IRQ_event+0x18/0x70
Nov 17 00:39:24 localhost kernel: [17197232.812000]  EFLAGS: 00200246    Tainted: P       (2.6.15-27-686)
Nov 17 00:39:24 localhost kernel: [17197232.812000] EAX: 00000001 EBX: df8a3820 ECX: df8a3820 EDX: c03a7f80
Nov 17 00:39:24 localhost kernel: [17197232.812000] ESI: 00000000 EDI: c03a7f80 EBP: c03a113c DS: 007b ES: 007b
Nov 17 00:39:24 localhost kernel: [17197232.812000] CR0: 8005003b CR2: 080a1dd0 CR3: 2a3c6000 CR4: 00000690
Nov 17 00:39:24 localhost kernel: [17197232.812000]  [__do_IRQ+157/272] __do_IRQ+0x9d/0x110
Nov 17 00:39:24 localhost kernel: [17197232.812000]  [do_IRQ+25/48] do_IRQ+0x19/0x30
Nov 17 00:39:24 localhost kernel: [17197232.812000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20
Nov 17 00:39:24 localhost kernel: [17197232.812000]  [pg0+943861403/1069167616] acpi_processor_idle+0x184/0x32d [processor]
Nov 17 00:39:24 localhost kernel: [17197232.812000]  [cpu_idle+111/192] cpu_idle+0x6f/0xc0
Nov 17 00:39:24 localhost kernel: [17197232.812000]  [start_kernel+415/512] start_kernel+0x19f/0x200
Nov 17 00:39:24 localhost kernel: [17197232.812000]  [unknown_bootoption+0/496] unknown_bootoption+0x0/0x1f0
Nov 17 00:40:01 localhost kernel: [17197269.596000] BUG: soft lockup detected on CPU#0!
Nov 17 00:40:09 localhost kernel: [17197269.596000]
Nov 17 00:40:09 localhost kernel: [17197269.596000] Pid: 0, comm:              swapper
Nov 17 00:40:09 localhost kernel: [17197269.596000] EIP: 0060:[handle_IRQ_event+24/112] CPU: 0
Nov 17 00:40:09 localhost kernel: [17197269.596000] EIP is at handle_IRQ_event+0x18/0x70
Nov 17 00:40:09 localhost kernel: [17197269.596000]  EFLAGS: 00000246    Tainted: P       (2.6.15-27-686)
Nov 17 00:40:09 localhost kernel: [17197269.596000] EAX: 00000001 EBX: df8a3820 ECX: df8a3820 EDX: c03a7f80
Nov 17 00:40:09 localhost kernel: [17197269.596000] ESI: 00000000 EDI: c03a7f80 EBP: c03a113c DS: 007b ES: 007b
Nov 17 00:40:09 localhost kernel: [17197269.596000] CR0: 8005003b CR2: b0bad000 CR3: 106fd000 CR4: 00000690
Nov 17 00:40:09 localhost kernel: [17197269.596000]  [__do_IRQ+157/272] __do_IRQ+0x9d/0x110
Nov 17 00:40:09 localhost kernel: [17197269.596000]  [do_IRQ+25/48] do_IRQ+0x19/0x30
Nov 17 00:40:09 localhost kernel: [17197269.596000]  [common_interrupt+26/32] common_interrupt+0x1a/0x20
Nov 17 00:40:09 localhost kernel: [17197269.596000]  [pg0+943861403/1069167616] acpi_processor_idle+0x184/0x32d [processor]
Nov 17 00:40:09 localhost kernel: [17197269.596000]  [cpu_idle+111/192] cpu_idle+0x6f/0xc0
Nov 17 00:40:09 localhost kernel: [17197269.596000]  [start_kernel+415/512] start_kernel+0x19f/0x200
Nov 17 00:40:09 localhost kernel: [17197269.596000]  [unknown_bootoption+0/496] unknown_bootoption+0x0/0x1f0

also:

Nov 17 00:50:52 localhost kernel: [17197921.200000] apm: BIOS not found.

---

### Post by Cannaregio on 2007-03-28
This comes very late for your problem, seen that you posted months ago, yet similar things happened to me and the following could be useful for people with similar problems. Maybe.

```
BUG: soft lockup detected on CPU#0!
```

Happens imho
[LIST]
[*]when you have a dual boot config
[*]when you TURNED YOUR WIRELESS OFF inLinux
[*]when you did reboot in windows after that
[*]when you now tried to reboot in linux with wireless still off
[/LIST]

Solution (worked for me)
[LIST]
[*]Reboot in windows
[*]Return wireless on
[*]shutdown windoze and reboot linux
[/LIST]

So the point is to RESET WIRELESS ON.
Why this kind of bug/error 
should be/could be/probably is 
related with wireless beats me.

(this rig was 2.6.17-11-generic, 3945 ABG Intel wireless, ubuntu edgy on a Siemens Amilo S that has an annoying flashing wireless light that you always like to turn off if there's no connection even if it is actually not necessary: let it flash and avoid the problem)

---

