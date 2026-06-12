---
title: "Lenovo L520 multiple Errors"
date: 2012-12-23
forum: Hardware
---

### Post by Theodor3 on 2012-12-23
Hello,

I've got quite some problem getting ubuntu to work under Lenovo L520.

First ubuntu installation was Ubuntu 11.10. there the common acpi problems occurred
as well as system crashes because of GPU overheating.
This was fixed with BIOS-update and "noapic"-Flag.
Computer would not shutdown in the last runlevel.

After some more errors, one very persistent one which just regularly warned that something wrong just happened with the hardware (thought no freeze or crash was detected) we tried to fix the system by installing 12.10 (after trying 12.04 with no result).

[B]Installing 12.10 with hard drive encryption
[/B]The installation itself would work but the encryption password was altered. No way to log in.

[B]12.10 without hard drive encryption
[/B]Boot worked but still system froze regularly and games would crash after some time.

So we tried a memtest resulted in broken ram (the lenovo diagnostics did not show this)
Contacted lenovo got new ram, but memtest showed that all ram banks where broken starting at exactly the same address.

Send in the Laptop, to repair but lenovo could not find anything wrong with the machine and send it back.

So we still got following errors under ubuntu:

[LIST]
[*]Memtest shows broken RAM
[*]System freezes
[*]Games crash
[/LIST]
while Windows XP works fine.




Im sorry i can't attach the log files (because the owner installed xp lately) but i will try to get some more information.

so my questions:

[LIST]
[*]What does this memtest indicate?
[*]Did somebody encountered same problems on L520
[*]And why is 12.10 encryption failing.
[/LIST]

---

