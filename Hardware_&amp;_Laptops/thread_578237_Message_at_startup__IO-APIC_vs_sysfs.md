---
title: "Message at startup : IO-APIC vs sysfs"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by ennoreys on 2007-10-17
Hello,

I've a little problem on my Asus A6T laptop at startup (ubuntu 7.04).

If I change nothing to menu.lst, I have the following message : "8254 : timer not connected IO-ACPI". Don't know if it's a real problem because laptop will boot properly and everything seems to work fine.
To fix this, I used the "noapic" and "nolapic" options in menu.lst. Again don't know consequences of these options (I'm new to ubuntu) but this time, USB devices have problems to be detected sometimes (randomly), which is annoying. Message at the beginning disappeared.
Then I read in some other forums to use "acpi=noirq" instead. I receive at startup following messages : "[    0.145472] pci 0000:00:03.0: Error creating sysfs bridge symlink, continuing...", 4 times. Everything seems to work fine, including USB. So I let this later option but not sure "sysfs" messages are important or not.

I also used apicmaintimer and pci=assign-busses but don't see any difference with or without.

Could you help me on this ?

---

### Post by ennoreys on 2007-10-17
Any help ?

---

