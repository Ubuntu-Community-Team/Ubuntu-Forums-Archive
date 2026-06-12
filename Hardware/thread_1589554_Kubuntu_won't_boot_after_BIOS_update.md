---
title: "Kubuntu won't boot after BIOS update"
date: 2010-10-06
forum: Hardware
---

### Post by rainmaker74 on 2010-10-06
Hi everyone. I recently purchased a Toshiba Satellite A-505 laptop with an Core i7 CPU. I had some trouble installing Kubuntu 10.04 LTS. The instalation CD got to the menu, but when I selected Install the screen went black and crashed upon boot. But I got it to work by booting with kernel parameter pci=noacpi. So I installed Kubuntu and it worked fine. ACPI didn't work (I could't monitor battery state or use the Fn key), but it didn't bother me much. I've read that problems but ACPI are frequent with Toshiba laptops due to their buggy ACPI implementations, and that it's possible to solve this problem by overriding the buggy BIOS DSDT with a custom one, but I haven't given it a try yet.
Some days ago I saw there was a BIOS update from Toshiba and I installed it, thinking that maybe it would solve the ACPI issue. Big mistake. Now linux won't boot. I tried several kernel parameters such as acpi=off, acpi=noirq, acpi=ht, pci=noacpi, pci=nobios, pci=biosirq, but none of it makes a difference. In most cases I get a lot of nasty AE_BAD_PARAMETER errors upon boot and the machine freezes. Only with acpi=ht it seems to get past that point with no errors, but it freezes later. I also tried without any special kernel parameters just in case. This happens with kernel 2.6.32.21-generic. I also tried 2.6.32.24-generic with no succes.
I've read about a lot of people with the same problem who solved it by flashing the old BIOS back. That obviously works but I'd rather avoid it if possible. The horror stories I've read about BIOS flashes rendering the laptop useless don't encourage me to do it at all. If I had known them from the beginning I would't have updated BIOS in the first place.
So my  question is, does anyone know a way to get my computer to boot without flashing the old BIOS? I don't care it X doesn't work or if performance is reduced. Just to have a working terminal would be better than this, since it would allow me to try the DSDT hack.

Thanks in advance

---

