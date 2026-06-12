---
title: "PCI card recognized (lspci) on one MB, not another"
date: 2014-07-22
forum: Hardware
---

### Post by maherhome on 2014-07-22
Hi,

I can't see a PCI card via lspci or lshw on an HP Z230 running 12.04 but it's seen fine on older PC also running 12.04.  The Z230 had an unorthodox install because I installed ZFS on the root partition; this entails bootstrapping with ubuntu-minimal and then installing ubuntu-desktop.  Also, the PCI card is a true PCI card in a PCI slot, not a PCIe card.  It's kind of a custom PCI card (from Astrocam) but at the heart is a Motorola DSP, and that's what lspci calls it on the older PC.

HP has "linux drivers" but only in SUSE and RH iso images.  If worst comes to worse I may try to alien those onto the system (a stab in the dark, really).

My belief, which may not be true, is that Linux has drivers for every "commodity" thing on a MB and I shouldn't need HP drivers (unless there's a custom HP chip or something) (?)   So perhaps I need some drivers from Ubuntu ~14?  I'm not sure how to go about grabbing the right stuff.

Or perhaps ubuntu-minimal + ubunut-desktop didn't install all the hardware drivers I need?

Any help is appreciated -

Steve

---

### Post by maherhome on 2014-07-22
[FONT=arial]Here's a lshw entry of the card on the OLD pc:

       *-pci:7[/FONT]
[FONT=arial]             description: PCI bridge[/FONT]
[FONT=arial]             product: 82801 PCI Bridge[/FONT]
[FONT=arial]             vendor: Intel Corporation[/FONT]
[FONT=arial]             physical id: 1e[/FONT]
[FONT=arial]             bus info: pci@0000:00:1e.0[/FONT]
[FONT=arial]             version: 90[/FONT]
[FONT=arial]             width: 32 bits[/FONT]
[FONT=arial]             clock: 33MHz[/FONT]
[FONT=arial]             capabilities: pci subtractive_decode bus_master cap_list[/FONT]
[FONT=arial]             resources: ioport:d000(size=4096) memory:fd400000-fd4fffff ioport:fd300000(size=1048576)[/FONT]
[FONT=arial]           *-multimedia[/FONT]
[FONT=arial]                description: Multimedia controller[/FONT]
[FONT=arial]                product: DSP56301 Digital Signal Processor[/FONT]
[FONT=arial]                vendor: Motorola[/FONT]
[FONT=arial]                physical id: 1[/FONT]
[FONT=arial]                bus info: pci@0000:08:01.0[/FONT]
[FONT=arial]                version: 03[/FONT]
[FONT=arial]                width: 32 bits[/FONT]
[FONT=arial]                clock: 33MHz[/FONT]
[FONT=arial]                capabilities: bus_master[/FONT]
[FONT=arial]                configuration: driver=mce_dsp latency=32[/FONT]
[FONT=arial]                resources: irq:17 memory:fd4f0000-fd4fffff[/FONT]

---

