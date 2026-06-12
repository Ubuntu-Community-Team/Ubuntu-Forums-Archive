---
title: "'Disabled IRQ 11' is this bad?"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by encompass on 2006-04-13
I noticed that after warm rebooting.. I sometimes get a 'Disabling irq 11' messege... I did a 
> dmesg | grep 11 
and got this...
> [4294669.344000] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 7 10 *11)
[4294669.345000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7 10 *11)
[4294669.347000] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 7 10 11)
[4294669.411000] audit: initializing netlink socket (disabled)
[4294669.411000] audit: initialized
[4294669.411000] VFS: Disk quotas dquot_6.5.1
[4294669.411000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.411000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.411000] devfs: boot_options: 0x0
[4294675.757000] Linux Tulip driver version 1.1.13 (May 11, 2002)
[4294675.757000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294675.757000] PCI: setting IRQ 11 as level-triggered
[4294675.757000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294675.763000] eth0: ADMtek Comet rev 17 at 00011c00, 00:D0:59:6A:FA:B4, IRQ 11.
[4294712.936000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294712.937000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294713.480000] irq 11: nobody cared (try booting with the "irqpoll" option.
[4294713.480000]  [<c011cf17>] __do_softirq+0x2f/0x91
[4294713.480000]  [<c011cf9f>] do_softirq+0x26/0x28
[4294713.480000]  [<c0211142>] driver_probe_device+0x2f/0x7a
[4294713.480000]  [<c0211276>] driver_attach+0x4d/0x8c
[4294713.480000]  [<c0211796>] bus_add_driver+0x98/0xd9
[4294713.480000]  [<c0131630>] sys_init_module+0x11e/0x19c
[4294713.480000] Disabling IRQ #11
[4294714.191000] irq 11: nobody cared (try booting with the "irqpoll" option.
[4294714.191000]  [<c011cf17>] __do_softirq+0x2f/0x91
[4294714.191000]  [<c011cf9f>] do_softirq+0x26/0x28
[4294714.191000]  [<c0211142>] driver_probe_device+0x2f/0x7a
[4294714.191000]  [<c0211276>] driver_attach+0x4d/0x8c
[4294714.191000]  [<c0211796>] bus_add_driver+0x98/0xd9
[4294714.191000]  [<c0131630>] sys_init_module+0x11e/0x19c
[4294714.191000] Disabling IRQ #11
[4294714.312000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
[4294714.359000] ACPI: PCI Interrupt 0000:00:04.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11

It used to be that when I has my old rtl8180 card plugged in if I saw that my wireless would not work... but I have changed cards, cause the old one has bad support right now.  And got a different one and it works fine when I get the message.  I have checked other devices like my sound and they all seem ok to me.
Any ideas if this is something I should be worried aobut?

---

### Post by towsonu2003 on 2006-04-13
as long as everything is working, I believe it's fine. I occasionally have this as well on irq #5 (used to have it all the time with suse and slackware). Try to check what that irq is related to (I think that info is in /proc) and double check if that device is working. I'd predict either wifi or winmodem.

---

### Post by encompass on 2006-04-14
Thanks, I didn't think it was a problem either... it may be my eth0...
jsut a quick:> ls /proc/irq/11/
shows yenta (my pcmcia) and eth0 my network card.
It is a fact that I have not been able to connect to my wireless when my etho is connected.  So it just may well be that it is my modem that is trying to get inthere at boot... but gets, well booted out. :P  thanks for you help.  And you have a cute dog.

---

### Post by towsonu2003 on 2006-04-14
> **encompass]
It is a fact that I have not been able to connect to my wireless when my etho is connected.[/QUOTE]
That's normal. it won't say in wikis explicitly, but they assume you'll take down one interface (eth0) before using the other (wlan0). That is usually a pain bc people (including me) tend to miss that and think wireless isn't working. 

is it possible it won't let you use eth0 and a plug and play pcmcia card at the same time? just a thought... hmm, may be not, bc my irq5 has winmodem + sound, but they work at the same time even when the "disabling irq" message is given. 

oh, well, as long as it's not broken, don't fix it  said:**
> And you have a cute dogheheh thanks a lot. I'll let him know :)

---

