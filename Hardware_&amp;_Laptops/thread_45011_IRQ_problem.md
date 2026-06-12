---
title: "IRQ problem"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by enrico on 2005-06-28
My randomly have this problem (from syslogd):
---
Jun  9 20:30:58 localhost kernel:  [__report_bad_irq+49/115] __report_bad_irq+0x31/0x73
Jun  9 20:30:58 localhost kernel:  [note_interrupt+76/111] note_interrupt+0x4c/0x6f
Jun  9 20:30:58 localhost kernel:  [do_IRQ+146/249] do_IRQ+0x92/0xf9
Jun  9 20:30:58 localhost kernel:  [common_interrupt+24/32] common_interrupt+0x18/0x20
Jun  9 20:30:58 localhost kernel:  [__crc_seq_read+7286078/8342461] acpi_processor_idle+0xd2/0x1c1 [processor]
Jun  9 20:30:58 localhost kernel:  [cpu_idle+29/50] cpu_idle+0x1d/0x32
Jun  9 20:30:58 localhost kernel:  [start_kernel+403/407] start_kernel+0x193/0x197
-----

it seems to be an internal modem problem.
When i have is problem i have to ctrl-alt-backspace and reboot

My system is an HP nx9030

any hint?

---

