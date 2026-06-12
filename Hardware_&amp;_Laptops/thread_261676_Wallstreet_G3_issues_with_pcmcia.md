---
title: "Wallstreet G3 issues with pcmcia"
date: 2006-09-20
forum: Hardware &amp; Laptops
---

### Post by brawnyllama on 2006-09-20
First post.

I was able to get Dapper Drake running in June on my G3 powerbook 'Wallstreet' model. and after some early migration issues is working very well. My goal was always to take this to being a rugged coffeehouse machine, so wireless is generally needed. After shaking many trees, I found a Dell TrueMobile 1150 series wifi card (rebranded ORiNOCO Lucent 'Hermes'). I was able to get this card to recognize and connect through the OS9 system that launches Ubuntu, verifying that the hardware Should work in this box. I believe that the problem is in detecting pcmcia memory in the slot. Can anyone of the kindest Ubuntu gurus there help? (My take is that ubuntu users are the kindest of anti-RTFM peeps out in linuxland)

Where do I need to check?
brawnyllama

I am running 6.06 with Kernel 2.6.15-26-powerpc
excerpt from /var/log/messages that seems to blow up when booting with the card in.
============================
Sep 18 15:02:17 localhost kernel: [  101.129733] ts: Compaq touchscreen protocol output
Sep 18 15:02:17 localhost kernel: [  111.298158] Yenta: CardBus bridge found at 0000:00:13.0 [0000:0000]
Sep 18 15:02:17 localhost kernel: [  111.307076] PCI: Bus 1, cardbus bridge: 0000:00:13.0
Sep 18 15:02:17 localhost kernel: [  111.315682]   IO window: 00001000-000011ff
Sep 18 15:02:17 localhost kernel: [  111.324191]   IO window: 00001400-000015ff
Sep 18 15:02:17 localhost kernel: [  111.332538]   PREFETCH window: 80400000-807fffff
Sep 18 15:02:17 localhost kernel: [  111.340814]   MEM window: 80800000-80bfffff
Sep 18 15:02:17 localhost kernel: [  111.349254] Yenta: ISA IRQ mask 0x0000, PCI irq 22
Sep 18 15:02:17 localhost kernel: [  111.357643] Socket status: 30000459
Sep 18 15:02:17 localhost kernel: [  111.366119] pcmcia: parent PCI bridge I/O window: 0x0 - 0x7fffff
Sep 18 15:02:17 localhost kernel: [  111.374854] pcmcia: parent PCI bridge Memory window: 0x80000000 - 0xfcffffff
Sep 18 15:02:17 localhost kernel: [  111.383644] pcmcia: parent PCI bridge Memory window: 0xfd000000 - 0xfdffffff
Sep 18 15:02:17 localhost kernel: [  111.392718] Yenta: CardBus bridge found at 0000:00:13.1 [0000:0000]
Sep 18 15:02:17 localhost kernel: [  111.401463] PCI: Bus 5, cardbus bridge: 0000:00:13.1
Sep 18 15:02:17 localhost kernel: [  111.410165]   IO window: 00001800-000019ff
Sep 18 15:02:17 localhost kernel: [  111.418873]   IO window: 00001c00-00001dff
Sep 18 15:02:17 localhost kernel: [  111.427462]   PREFETCH window: 80c00000-80ffffff
Sep 18 15:02:17 localhost kernel: [  111.435951]   MEM window: 81000000-813fffff
Sep 18 15:02:17 localhost kernel: [  111.686730] Yenta: ISA IRQ mask 0x0000, PCI irq 23
Sep 18 15:02:17 localhost kernel: [  111.695250] Socket status: 30000086
Sep 18 15:02:17 localhost kernel: [  111.703914] pcmcia: parent PCI bridge I/O window: 0x0 - 0x7fffff
Sep 18 15:02:17 localhost kernel: [  111.712295] pcmcia: parent PCI bridge Memory window: 0x80000000 - 0xfcffffff
Sep 18 15:02:17 localhost kernel: [  111.720579] pcmcia: parent PCI bridge Memory window: 0xfd000000 - 0xfdffffff
Sep 18 15:02:17 localhost kernel: [  112.364977] pccard: PCMCIA card inserted into slot 0
Sep 18 15:02:17 localhost kernel: [  112.560980] cs: memory probe 0x80000000-0xfcffffff: excluding 0x80000000-0x82ffffff 0xf3000000-0xf37fffff 0xf4000000-0xf47fffff
Sep 18 15:02:17 localhost kernel: [  112.688047] cs: memory probe 0xfd000000-0xfdffffff:Machine check in kernel mode.
Sep 18 15:02:17 localhost kernel: [  112.697085] Caused by (from SRR1=49030): Transfer error ack signal
Sep 18 15:02:17 localhost kernel: [  112.706175] Oops: Machine check, sig: 7 [#1]
Sep 18 15:02:17 localhost kernel: [  112.715116] Modules linked in: pcmcia yenta_socket rsrc_nonstatic pcmcia_core evdev tsdev ext3 jbd ide_disk ide_cd cdrom i2c_keywest capability commoncap
==================================

---

### Post by richaoj on 2007-06-01
I am having the same problem. any resolution for this?

---

