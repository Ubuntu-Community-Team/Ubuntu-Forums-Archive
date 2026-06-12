---
title: "irq 16: nobody cared (try booting with the &quot;irqpoll&quot; option)"
date: 2011-10-12
forum: Hardware
---

### Post by mdfakkeer on 2011-10-12
I have a storage server with Highpoint Rocket Raid card and 16 *2 TB HDD's . Ubuntu 10.04 64 bit server edition is running. My machine is very slow data transfer speed after getting the following error . I don't know what is the meaning of the following error?. if any body knows please help me to solve the issue.
 
dmesg error
 
[92815.199124] irq 16: nobody cared (try booting with the "irqpoll" option)
[92815.199652] Pid: 0, comm: swapper Tainted: P 2.6.32-24-server #39-Ubuntu
[92815.199654] Call Trace:
[92815.199656] <IRQ> [<ffffffff810c69eb>] __report_bad_irq+0x2b/0xa0
[92815.199667] [<ffffffff810c6bec>] note_interrupt+0x18c/0x1d0
[92815.199673] [<ffffffff81019e79>] ? read_tsc+0x9/0x20
[92815.199676] [<ffffffff810c72ed>] handle_fasteoi_irq+0xdd/0x100
[92815.199680] [<ffffffff81015d12>] handle_irq+0x22/0x30
[92815.199685] [<ffffffff8155fc6c>] do_IRQ+0x6c/0xf0
[92815.199688] [<ffffffff81013b13>] ret_from_intr+0x0/0x11
[92815.199690] <EOI> [<ffffffff8130f0fb>] ? acpi_idle_enter_c1+0xa3/0xc1
[92815.199698] [<ffffffff8130f0da>] ? acpi_idle_enter_c1+0x82/0xc1
[92815.199703] [<ffffffff8144df67>] ? cpuidle_idle_call+0xa7/0x140
[92815.199707] [<ffffffff81011e63>] ? cpu_idle+0xb3/0x110
[92815.199711] [<ffffffff81552a83>] ? start_secondary+0xa8/0xaa
[92815.199712] handlers:
[92815.199921] [<ffffffffa0002be0>] (hpt_intr+0x0/0x80 [rr274x_3x])
[92815.200509] [<ffffffffa0002be0>] (hpt_intr+0x0/0x80 [rr274x_3x])
[92815.201069] Disabling IRQ #16
[92817.789747] rr274x_3x[IMG]http://static.linuxquestions.org/questions/images/smilies/biggrin.gif[/IMG]evice error information 0x1000000
[92817.789754] rr274x_3x:Task file error, StatusReg=0x51, ErrReg=0x4, LBA[0-3]=0xaaa3f,LBA[4-7]=0x0

---

### Post by mdfakkeer on 2012-01-23
Any update information about my posted issue?

---

