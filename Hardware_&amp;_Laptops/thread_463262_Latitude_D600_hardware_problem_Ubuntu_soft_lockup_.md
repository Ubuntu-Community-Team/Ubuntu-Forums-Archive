---
title: "Latitude D600 hardware problem? Ubuntu soft_lockup and Windows blue screen"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by kopts on 2007-06-03
My Dell Latitude D600 started to show problems just a couple of weeks after its warranty ended :(
Ubunty (Feisty with 2.6.20-15) started to freeze, sometimes completely (reboot required), 
sometimes by entering a periodic cycle of freezing for 10-11 sec and unfreezing for 1-2 sec
(the syslog message is below). The system enters this at arbitrary time, may be running OK for 
an hour or for a few minutes. Windows never shows this pattern, but it started to go blue screen,
also at irregular times. A couple of times BIOS clock got reset. All this started to happen with both
OSes a few months after the laptop was dropped on the concrete floor (i.e. it worked fine for 
a few months after the fall). 

I have not replaced the BIOS battery, the machine is only a bit more that 3 years old,
but I believe battery cannot cause such behaviour anyway.

I infer it should be a hardware problem. Does anybody have any idea whether anything 
can be done to make the machine work?

Thanks!
A.

Kernel message:

Jun  3 14:18:40 pyosik kernel: [  213.836000]  [softlockup_tick+156/240] softlockup_tick+0x9c/0xf0
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [update_process_times+51/128] update_process_times+0x33/0x80
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [timer_interrupt+133/176] timer_interrupt+0x85/0xb0
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [handle_level_irq+141/288] handle_level_irq+0x8d/0x120
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [<e0919db0>] tg3_timer+0x0/0x810 [tg3]
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [do_IRQ+64/128] do_IRQ+0x40/0x80
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [do_IRQ+69/128] do_IRQ+0x45/0x80
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [<e0919db0>] tg3_timer+0x0/0x810 [tg3]
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [<e0919db0>] tg3_timer+0x0/0x810 [tg3]
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [<e09100d8>] tg3_setup_phy+0x528/0xe70 [tg3]
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [native_read_tsc+2/16] native_read_tsc+0x2/0x10
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [delay_tsc+24/48] delay_tsc+0x18/0x30
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [__delay+6/16] __delay+0x6/0x10
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [<e090c2f6>] tg3_readphy+0x66/0x100 [tg3]
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [<e090f179>] tg3_setup_copper_phy+0x1c9/0xc00 [tg3]
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [signal_wake_up+30/48] signal_wake_up+0x1e/0x30
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [<e0919db0>] tg3_timer+0x0/0x810 [tg3]
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [<e090fd68>] tg3_setup_phy+0x1b8/0xe70 [tg3]
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [enqueue_hrtimer+76/128] enqueue_hrtimer+0x4c/0x80
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [<e0919db0>] tg3_timer+0x0/0x810 [tg3]
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [<e091a43c>] tg3_timer+0x68c/0x810 [tg3]
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [run_timer_softirq+303/416] run_timer_softirq+0x12f/0x1a0
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [__do_softirq+130/256] __do_softirq+0x82/0x100
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [do_softirq+85/96] do_softirq+0x55/0x60
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [do_IRQ+69/128] do_IRQ+0x45/0x80
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [acpi_ds_load2_end_op+180/721] acpi_ds_load2_end_op+0xb4/0x2d1
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [<e08317e2>] acpi_processor_idle+0x225/0x3f7 [processor]
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [cpu_idle+73/208] cpu_idle+0x49/0xd0
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [start_kernel+869/1056] start_kernel+0x365/0x420
Jun  3 14:18:40 pyosik kernel: [  213.836000]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
Jun  3 14:18:40 pyosik kernel: [  213.836000]  =======================

---

### Post by adampyre on 2007-06-05
Sounds like a hardware issue to me. Is the cooling fan still running? You may want to play with i8kfangui (dellfand) to test your fans out and see if cooling your laptop fixes this. Good luck.

---

