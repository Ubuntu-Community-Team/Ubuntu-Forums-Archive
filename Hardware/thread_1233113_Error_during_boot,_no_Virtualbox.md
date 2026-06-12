---
title: "Error during boot, no Virtualbox"
date: 2009-08-06
forum: Hardware
---

### Post by zee on 2009-08-06
Hi.
  I have a 4-core computer with a recent (2 weeks) install of Ubuntu 9.04.

  Upon boot I noticed this error:
Aug  6 15:10:24 ser kernel: [   12.775815] resource map sanity check conflict: 0xffb00000 0xffffffff 0xfff80000 0xffffffff reserved
Aug  6 15:10:24 ser kernel: [   12.775824] ------------[ cut here ]------------
Aug  6 15:10:24 ser kernel: [   12.775827] WARNING: at /build/buildd/linux-2.6.28/arch/x86/mm/ioremap.c:226 __ioremap_caller+0x349/0x390()
Aug  6 15:10:24 ser kernel: [   12.775829] Modules linked in: ck804xrom(+) mtd chipreg serio_raw nvidia(P+) map_funcs i2c_nforce2 pcspkr reiserfs forcedeth usbhid floppy raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear fbcon tileblit font bitblit softcursor
Aug  6 15:10:24 ser kernel: [   12.775847] Pid: 1103, comm: modprobe Tainted: P           2.6.28-14-generic #47-Ubuntu
Aug  6 15:10:24 ser kernel: [   12.775849] Call Trace:
Aug  6 15:10:24 ser kernel: [   12.775856]  [<ffffffff80250a4f>] warn_on_slowpath+0x5f/0x90
Aug  6 15:10:24 ser kernel: [   12.775860]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
Aug  6 15:10:24 ser kernel: [   12.775862]  [<ffffffff8022f669>] ? default_spin_lock_flags+0x9/0x10
Aug  6 15:10:24 ser kernel: [   12.775865]  [<ffffffff80236c29>] __ioremap_caller+0x349/0x390
Aug  6 15:10:24 ser kernel: [   12.775869]  [<ffffffffa08fd2db>] ? ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
Aug  6 15:10:24 ser kernel: [   12.775872]  [<ffffffff80236d82>] ioremap_nocache+0x12/0x20
Aug  6 15:10:24 ser kernel: [   12.775876]  [<ffffffffa08fd2db>] ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
Aug  6 15:10:24 ser kernel: [   12.775879]  [<ffffffffa0903041>] init_ck804xrom+0x41/0x59 [ck804xrom]
Aug  6 15:10:24 ser kernel: [   12.775882]  [<ffffffffa0903000>] ? init_ck804xrom+0x0/0x59 [ck804xrom]
Aug  6 15:10:24 ser kernel: [   12.775885]  [<ffffffff8020a03b>] do_one_initcall+0x3b/0x170
Aug  6 15:10:24 ser kernel: [   12.775890]  [<ffffffff802424e2>] ? enqueue_entity+0x122/0x2b0
Aug  6 15:10:24 ser kernel: [   12.775894]  [<ffffffff80225fca>] ? native_smp_send_reschedule+0x3a/0x50
Aug  6 15:10:24 ser kernel: [   12.775897]  [<ffffffff802481c6>] ? resched_task+0x76/0x90
Aug  6 15:10:24 ser kernel: [   12.775899]  [<ffffffff8024a41c>] ? try_to_wake_up+0x12c/0x2e0
Aug  6 15:10:24 ser kernel: [   12.775905]  [<ffffffff8027f16d>] sys_init_module+0xad/0x1e0
Aug  6 15:10:24 ser kernel: [   12.775908]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
Aug  6 15:10:24 ser kernel: [   12.775910] ---[ end trace 05dcf78cf7531f86 ]---

What does it mean? SW/HW problem?

The system appears to bw working as expected, only VirtualBox does not work, because the startup script is unable to load the models needed.

Thanks in advance!

---

