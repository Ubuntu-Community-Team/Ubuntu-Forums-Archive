---
title: "APIC error on CPU0: 00(40)"
date: 2008-12-30
forum: Hardware
---

### Post by nils154 on 2008-12-30
I have a Gateway MX6450 AMD Turion 64, Ubuntu 8.04 (32 bit).
The system seems to freeze after being idle for a long time.
The last line in the /var/log/debug is typically: APIC error on CPU0,
sometimes with a few more messages that the wireless network is
no longer responsive. The wireless bars are also showing no signal.

What is the problem?

-Nils

---

### Post by teaker1s on 2008-12-30
there are several bugs listed on this, first check for bios update. 
Secondly you may find that boot options could solve it as it's acpi related.

1. Updating the BIOS
2. booting with options such as -noapic on the GRUB kernel line

---

### Post by nils154 on 2008-12-30
> **teaker1s said:**
> there are several bugs listed on this, first check for bios update. 
Secondly you may find that boot options could solve it as it's acpi related.

1. Updating the BIOS
2. booting with options such as -noapic on the GRUB kernel line
Thanks. Just updated BIOS to 68.05. Will wait for a couple of hours to see if it still freezes. Then I will try the boot options.

-Nils

---

### Post by nils154 on 2009-02-28
I am still trying to solve my freezing problem. The laptop frequently freezes sometime in the middle of the night, but it has also been fine for over a week.
tried disabling APIC in the boot procedure, but laptop won't boot at all then.
Looks like the /var/log/messages is trying to tell me something, but I don't know what is.

Thanks for any suggestions.

---

