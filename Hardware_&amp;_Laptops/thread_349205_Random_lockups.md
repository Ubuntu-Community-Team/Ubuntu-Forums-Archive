---
title: "Random lockups"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by wiz561 on 2007-01-29
Hi,

   I installed Edgy the other day and now I'm running into some problems.  I had to use nosmp and noapic in the grub menu.  This seems to fix it, but then I loose my other cpu.  I had noapic in there and not nosmp when the lookups were occuring.  Here is a trace from dmesg...

[ 1665.810314] irq 7: nobody cared (try booting with the "irqpoll" option)
[ 1665.810322] 
[ 1665.810323] Call Trace: <IRQ> <ffffffff802b68a5>{__report_bad_irq+53}
[ 1665.810352]        <ffffffff802b6b20>{note_interrupt+544} <ffffffff880c6bb8>{:usbcore:usb_hcd_irq+40}
[ 1665.810389]        <ffffffff802b6190>{__do_IRQ+224} <ffffffff802737e2>{do_IRQ+66}
[ 1665.810399]        <ffffffff80271f00>{default_idle+0} <ffffffff80265d08>{ret_from_intr+0} <EOI>
[ 1665.810409]        <ffffffff80269d9f>{thread_return+0} <ffffffff80232690>{unix_poll+0}
[ 1665.810422]        <ffffffff80271f29>{default_idle+41} <ffffffff8024ecfe>{cpu_idle+158}
[ 1665.810432]        <ffffffff8060885b>{start_kernel+523} <ffffffff80608293>{_sinittext+659}
[ 1665.810444] handlers:
[ 1665.810446] [<ffffffff880c6b90>] (usb_hcd_irq+0x0/0x60 [usbcore])
[ 1665.810461] Disabling IRQ #7
[ 3532.929413] Losing some ticks... checking if CPU frequency changed.
[ 3581.657776] warning: many lost ticks.
[ 3581.657779] Your time source seems to be instable or some driver is hogging interupts
[ 3581.657787] rip vsysc2+0x7f/0x16c



I really have no clue what all of this means and is really the first time something like this has happened to me with linux.  Any help is appreciated.


Thanks,
Mike

---

