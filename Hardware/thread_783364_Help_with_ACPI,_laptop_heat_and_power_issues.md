---
title: "Help with ACPI, laptop heat and power issues"
date: 2008-05-05
forum: Hardware
---

### Post by spyderpride on 2008-05-05
I have a Gateway MT6456 with an AMD Turion X2 TL-52 CPU running Hardy.  The problem I am having is that my laptop drains its 8-cell battery in about an hour and a half and operates in the temperature range of 70-80 C. I can bring the CPU to 100% load and it stays in the same range, but the fan runs a lot more.  It's stuck in the C0 state.  Powertop tells me that I have 220+ "extra timer interrupts" at any given time and power consumption is 27 W at the lowest, usually above 30 W.

Here's the kicker: when I set acpi=off or noacpi, it runs at a decent 50-62 C and all the "extra timer interrupts" are gone. However... frequency scaling, battery info, and my network devices fail when I set this boot option.  There probably are other things not working, but these are what I have observed. I'm sure they depend on ACPI in some way or form (duh). Oh yeah, when I do this I also need to set pnpbios=off otherwise I get an error on boot that doesn't seem to affect anything.

I've contacted Gateway, AMD, and Phoenix (BIOS) about this and of course they have no idea. I would greatly appreciate any help with this. Let me know if I need to give more info.

EDIT: I also get the PCI BIOS BUG #81, which has no readily noticeable affects. I hear this is common with AMD CPU's and Phoenix BIOS.

---

