---
title: "USB key problem"
date: 2005-02-10
forum: Hardware &amp; Laptops
---

### Post by aurelien on 2005-02-10
Hello,

I've just installed an Ubuntu Warty on my laptop replacing a mandrake 10.1, but I'm still in trouble  with my USB key that causes an IRQ on my system  :-x 

the message return is :

[INDENT]irq 5: nobody cared!
[<c0108322>] __report_bad_irq+0x2a/0x8b
[<c010840c>] note_interrupt+0x6f/0x9f
[<c010871a>] do_IRQ+0x16d/0x19e
[<c01069f0>] common_interrupt+0x18/0x20
[<c012398a>] __do_softirq+0x42/0xaa
[<c0123a1f>] do_softirq+0x2d/0x2f
[<c01086f7>] do_IRQ+0x14a/0x19e
[<c01069f0>] common_interrupt+0x18/0x20
[<c010401e>] default_idle+0x0/0x2f
[<c010404a>] default_idle+0x2c/0x2f
[<c01040b3>] cpu_idle+0x33/0x3c
[<c0350875>] start_kernel+0x1c3/0x214
[<c0350309>] unknown_bootoption+0x0/0x149
handlers:
[<e0a54669>] (usb_hcd_irq+0x0/0x67 [usbcore])
[<e0b1780e>] (snd_intel8x0_interrupt+0x0/0x2a4 [snd_intel8x0])
[<e0b0b570>] (snd_intel8x0_interrupt+0x0/0x26f [snd_intel8x0m])
[<e0b9744d>] (SkGeIsrOnePort+0x0/0x14e [sk98lin])
[<e0b5e7f3>] (yenta_interrupt+0x0/0x39 [yenta_socket])
[<e0b86937>] (ohci_irq_handler+0x0/0x800 [ohci1394])
Disabling IRQ #5
[/INDENT]

But I don't understand the problem involved, this key  work on my mandrake.

I have a usb mouse that works perfectly.

I also had an error about pnpbios, but when I solve it using the boot option pnpbios=off, nothing change

Can you help?

Thank you

Aurelien

---

