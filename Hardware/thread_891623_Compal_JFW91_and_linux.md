---
title: "Compal JFW91 and linux"
date: 2008-08-16
forum: Hardware
---

### Post by tetrodetube on 2008-08-16
Being a long-term desktop ubuntu user, I decided to also install ubuntu on my laptop based on Compal JFW91 with Intel T5750 2-core processor. ([http://www.compal.com/Product/Html/notebook/JFW91.htm]("http://www.compal.com/Product/Html/notebook/JFW91.htm"))

The difficulties started soon. 8.04 live cd didn't boot, the orange bar stopped in the middle and the computer hanged. 
Trying 6.06 instead  I got only some flickers on the screen. 

Reading the earlier topics I thought that the problem is in missing graphic support and tried the 8.04 alternative installation cd, but after choosing "install" from the menu, I saw only a blinking cursor. 

Opensuse 10.3, which also shows boot processes, hanged at "loading basic drivers".

So, what is the problem and is it solvable?

---

### Post by axmachado on 2008-08-28
Hello, people

A Brazilian company called Intelbras sells this machine using their own brand, and I've managed to put it to work... partially

The problem is somewhat related with APIC and IRQ routing in SMP mode. It's possible to run linux on that in two ways:

* boot with "noapic" and "acpi=off" options, disabling all power control functinons (you will be unable to see the battery charge level, for example)

* boot with "nosmp" option or use a non SMP kernel. It will make your dual core machine works as a single core one.

I think it can be a bios problem, or even a hardware problem. Compal does not provide a bios upgrade.

Hope it helps

Alexandre

---

### Post by kuehlkamp on 2008-10-22
Thanks for the hint, Alexandre.
The same happens with another model from the same company, the i21. I was stuck in the same problem until after googling around for hours I found that the following boot parameters seem to make acpi and smp to work together:

noapic nolapic pci=assign-busses apicmaintimer idle=poll reboot=cold,hard

[]s

Andrey

---

