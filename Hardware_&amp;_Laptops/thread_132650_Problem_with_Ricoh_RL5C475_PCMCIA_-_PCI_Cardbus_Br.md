---
title: "Problem with Ricoh RL5C475 PCMCIA - PCI Cardbus Bridge"
date: 2006-02-18
forum: Hardware &amp; Laptops
---

### Post by Dlizzz on 2006-02-18
Hi All,

I'm desesperately trying to activate my Cardbus bridge in order to use my Belkin Pre-N network card (thru ndiswrapper 1.9). 

As shown by *dmesg* it seems that's a problem of memory allocation :

> [4294694.722000] Linux Kernel Card Services
[4294694.722000]   options:  [pci] [cardbus] [pm]
[4294694.729000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 22
[4294694.729000] Yenta: CardBus bridge found at 0000:02:02.0 [0000:0000]
[4294694.729000] yenta 0000:02:02.0: Preassigned resource 0 busy, reconfiguring...
[4294694.729000] yenta 0000:02:02.0: Preassigned resource 2 busy, reconfiguring...
[4294694.849000] Yenta: ISA IRQ mask 0x0000, PCI irq 22
[4294694.849000] Socket status: 30000820
[4294695.477000] PCI: Failed to allocate mem resource #1:80000@f3080000 for 0000:03:00.0
[4294695.477000] PCI: Failed to allocate mem resource #0:20000@f3020000 for 0000:03:00.0


I've tried many kernel options *(acpi=off noapic nolapic acpi=strict,noirq pci=biosirq,nosort,routeirq)* but nothing seems to work.

I'm currently using the *2.6.12-686-smp* kernel but I had exactly the same result with the *2.6.12-386*.

I've tried to modifiy the config file in */etc/pcmcia*, but it seems that it has no effect on 32 bits cards. In the *man* page they say that 32 bits cards are managed by hotplug.

I've linked some files, with my config, to this post.

Any ideas ? Thanks in advance....:-D

---

### Post by McLogic on 2006-04-24
Bump -- I'm having trouble with the same RL5c475 card. It is on an i815 with the standard i386 kernel.

---

### Post by gdburton on 2006-05-08
I have also noticed the same problem.](*,) 
I have been searching the net for possible answers.
So far the best starting point I have seen is
[http://www.raw-io.com/pci_802.11b.html]("http://www.raw-io.com/pci_802.11b.html")

However this refers to the 2.4 kernel. But it might trigger some more thoughts.

I'm a real newbie to Linux so am not yet ready for kernel re-compiles, but I thought I'd pass this on.

I do remember a numer of years back when I was working for a company trying to sell cards with this chip we had a major hassle getting the suppliers Windows drivers sorted out.

---

