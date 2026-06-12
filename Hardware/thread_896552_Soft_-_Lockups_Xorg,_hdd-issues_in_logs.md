---
title: "Soft - Lockups Xorg, hdd-issues in logs"
date: 2008-08-21
forum: Hardware
---

### Post by Richy on 2008-08-21
My computer tends to freeze lately and I finally found something in the logs. However, I don't know _what_ exactly is the problem. 

```

Aug 21 14:24:20 Mercur -- MARK --
Aug 21 14:44:20 Mercur -- MARK --
Aug 21 14:45:43 Mercur kernel: [28018.537312] Pid: 0, comm: swapper Tainted: P        2.6.24-19-generic #1
Aug 21 14:45:43 Mercur kernel: [28018.537314]
Aug 21 14:45:43 Mercur kernel: [28018.537315] Call Trace:
Aug 21 14:45:43 Mercur kernel: [28018.537317]  <IRQ>  [__report_bad_irq+0x1e/0x80] __report_bad_irq+0x1e/0x80
Aug 21 14:45:43 Mercur kernel: [28018.537344]  [note_interrupt+0x2ad/0x2e0] note_interrupt+0x2ad/0x2e0
n$g 21 14:45:43 Mercur kernel: [28018.537353]  [handle_fasteoi_irq+0xa1/0x110] handle_fasteoi_irq+0xa1/0x110
Aug 21 14:45:43 Mercur kernel: [28018.537361]  [do_IRQ+0x7b/0x100] do_IRQ+0x7b/0x100
n$g 21 14:45:43 Mercur kernel: [28018.537366]  [ret_from_intr+0x0/0x0a] ret_from_intr+0x0/0xa
Aug 21 14:45:43 Mercur kernel: [28018.537369]  <EOI>  [lapic_next_event+0x0/0x10] lapic_next_event+0x0/0x10
Aug 21 14:45:43 Mercur kernel: [28018.537383]  [tick_nohz_stop_sched_tick+0x1cb/0x2d0] tick_nohz_stop_sched_tick+0x1cb/0x2d0
Aug 21 14:45:43 Mercur kernel: [28018.537391]  [mwait_idle+0x0/0x50] mwait_idle+0x0/0x50
Aug 21 14:45:43 Mercur kernel: [28018.537395]  [default_idle+0x0/0x40] default_idle+0x0/0x40
Aug 21 14:45:43 Mercur kernel: [28018.537400]  [cpu_idle+0x41/0xc0] cpu_idle+0x41/0xc0
Aug 21 14:45:43 Mercur kernel: [28018.537407]  [start_kernel+0x2c5/0x350] start_kernel+0x2c5/0x350
Aug 21 14:45:43 Mercur kernel: [28018.537414]  [x86_64_start_kernel+0x12e/0x140] _sinittext+0x12e/0x140
Aug 21 14:45:43 Mercur kernel: [28018.537421]
Aug 21 14:46:29 Mercur kernel: [28063.749730]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Aug 21 14:46:29 Mercur kernel: [28063.749732]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 21 14:46:29 Mercur kernel: [28063.749753] ata9: soft resetting link
Aug 21 14:46:29 Mercur kernel: [28064.572950] ata9.00: configured for UDMA/33
Aug 21 14:46:29 Mercur kernel: [28064.744586] ata9.01: configured for UDMA/33
Aug 21 14:46:29 Mercur kernel: [28064.744595] ata9: EH complete
Aug 21 14:46:59 Mercur kernel: [28094.695477]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Aug 21 14:46:59 Mercur kernel: [28094.695478]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
.
.
.
.
Aug 21 14:49:03 Mercur kernel: [28218.478485] ata9: soft resetting link
Aug 21 14:49:04 Mercur kernel: [28219.301680] ata9.00: configured for UDMA/25
Aug 21 14:49:04 Mercur kernel: [28219.473315] ata9.01: configured for UDMA/33
Aug 21 14:49:04 Mercur kernel: [28219.473324] ata9: EH complete
Aug 21 14:49:34 Mercur kernel: [28249.424207]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Aug 21 14:49:34 Mercur kernel: [28249.424209]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Aug 21 14:49:34 Mercur kernel: [28249.424230] ata9: soft resetting link
Aug 21 14:49:35 Mercur kernel: [28250.247427] ata9.00: configured for UDMA/25
Aug 21 14:49:35 Mercur kernel: [28250.419061] ata9.01: configured for UDMA/33
Aug 21 14:49:35 Mercur kernel: [28250.419070] ata9: EH complete
Aug 21 14:50:05 Mercur kernel: [28280.369954]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Aug 21 14:50:05 Mercur kernel: [28280.369955]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
.
.
.
Aug 21 15:19:59 Mercur kernel: [30070.818410] ata9: soft resetting link
Aug 21 15:20:00 Mercur kernel: [30071.641686] ata9.00: configured for PIO0
Aug 21 15:20:00 Mercur kernel: [30071.813320] ata9.01: configured for UDMA/25
Aug 21 15:20:00 Mercur kernel: [30071.813329] ata9: EH complete
Aug 21 15:20:02 Mercur kernel: [30074.117072] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 21 15:20:03 Mercur exiting on signal 15
Aug 21 15:21:15 Mercur syslogd 1.5.0#1ubuntu1: restart.

```

so what's going on?


Richy

---

