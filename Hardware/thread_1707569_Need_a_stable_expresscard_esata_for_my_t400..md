---
title: "Need a stable expresscard esata for my t400."
date: 2011-03-15
forum: Hardware
---

### Post by liquidxit2 on 2011-03-15
Dont need any features other than stability. The drive will be connected to the t400 all day every day. I dont need hot swapping or anything fancy, rather just need an always on stable data connection to my external drive. 

Thanks!

---

### Post by locutus42 on 2011-06-18
I've got a JMicron express card 34 2 port SATA card working on Lucid.

If you want hotswap to work instead of only working from boot, load the ACPI hotswap driver( sudo modprobe acpiphp ). output from lspci shows this:

02:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) (prog-if 01)
        Subsystem: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller
        Flags: fast devsel, IRQ 16
        Capabilities: <access denied>
        Kernel modules: ahci

---

