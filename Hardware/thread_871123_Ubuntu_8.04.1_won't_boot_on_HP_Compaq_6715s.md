---
title: "Ubuntu 8.04.1 won't boot on HP Compaq 6715s"
date: 2008-07-26
forum: Hardware
---

### Post by use_R on 2008-07-26
I installed Ububntu 8.04.1 on HP Compaq 6715s with certain interventions (I selected noapic, nolapic, acpi=off during the installation).

But now it won't boot.

Some useful tip please? Tnx.

---

### Post by phidia on 2008-07-26
You may need to add those kernel boot options to /boot/grub/menu.lst 
But what error messages and/or other symptoms are you getting?

---

### Post by use_R on 2008-07-28
Thanks.
I solved it - I have edited /boot/grub/menu.lst file with additional parameters (noapic nolapic acpi=off) at the end of of a line that begins with "# defoptions=". NOw it boots, as well as new problem came - won't shut down (a screen with Ubuntu logo freezes when shutting down....). Btw, restart works (no freeze with Ubuntu logo on the screen). A useful tip please? Tnx.

---

### Post by malocchius on 2009-09-09
It won't turn off because the acpi is off. [http://www.helpwithpcs.com/jargon/acpi.htm](http://www.helpwithpcs.com/jargon/acpi.htm)

---

