---
title: "Jumpy/jittery mouse and disable IRQ #17"
date: 2013-01-23
forum: Hardware
---

### Post by tuuk on 2013-01-23
Every 5-6 boots, I end up with  a jittery/jumpy mouse (a wireless Logitech M235 mouse on a DELL Latitude E6510 laptop but other mice had the same problem as well). 

When the problem occurs and only then, the tail of dmesg output consistently contains the following lines. They must be the clue to the failure.

> 
[   51.156616] irq 17: nobody cared (try booting with the "irqpoll" option)
[   51.156623] Pid: 0, comm: swapper/1 Not tainted 3.5.0-22-generic #34-Ubuntu
[   51.156624] Call Trace:
[   51.156626]  <IRQ>  [<ffffffff810e17ed>] __report_bad_irq+0x3d/0xe0
[   51.156635]  [<ffffffff810e1af4>] note_interrupt+0x1b4/0x200
[   51.156642]  [<ffffffff810df2d7>] handle_irq_event_percpu+0xa7/0x1f0
[   51.156643]  [<ffffffff810df46e>] handle_irq_event+0x4e/0x80
[   51.156645]  [<ffffffff810e262a>] handle_fasteoi_irq+0x5a/0x100
[   51.156650]  [<ffffffff81015082>] handle_irq+0x22/0x40
[   51.156654]  [<ffffffff8168d96a>] do_IRQ+0x5a/0xe0
[   51.156657]  [<ffffffff81683f2a>] common_interrupt+0x6a/0x6a
[   51.156658]  <EOI>  [<ffffffff81390a8a>] ? intel_idle+0xea/0x150
[   51.156664]  [<ffffffff81390a6b>] ? intel_idle+0xcb/0x150
[   51.156668]  [<ffffffff81527f29>] cpuidle_enter+0x19/0x20
[   51.156669]  [<ffffffff81528559>] cpuidle_idle_call+0xa9/0x240
[   51.156672]  [<ffffffff8101c48f>] cpu_idle+0xaf/0x120
[   51.156676]  [<ffffffff8166c7f8>] start_secondary+0x1de/0x1e5
[   51.156677] handlers:
[   51.156681] [<ffffffff814b3400>] usb_hcd_irq
[   51.156682] Disabling IRQ #17
So, it must be something to do with the disabling of the IRQ #17.

I tried booting with irqpoll kernel option as suggested by the first line in the output above. I have not seen the problem when booted with the irqpoll option, but then within 10 minutes of booting, the system slowed down to an almost halt became very unresponsive.

Can anyone help? Is there any other information I can provide?

Thanks.
tuuk

---

