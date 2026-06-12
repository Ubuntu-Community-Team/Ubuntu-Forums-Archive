---
title: "Thinkpad T30 not producing ACPI Lid Event"
date: 2011-02-03
forum: Hardware
---

### Post by LenPayne on 2011-02-03
I'm running a Thinkpad T30 with xubuntu 10.10. Closing the lid produces no ACPI event.

The following procedure produces no result:
[LIST]
[*]run *acpi_listen*
[*]close the lid
[*]open the lid
[*]push the lid button with a pen
[*]watch nothing happen
[/LIST]

Every other ACPI event appears to function as normal, and produces an output on acpi_listen, but the lid does not.

Any ideas?

I am using the thinkpad_acpi kernel module with the 2.6.35-25-generic kernel.

---

