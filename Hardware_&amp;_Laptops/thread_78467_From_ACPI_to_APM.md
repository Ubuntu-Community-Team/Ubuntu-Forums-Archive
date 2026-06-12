---
title: "From ACPI to APM"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by posterlu on 2005-10-18
Hello!

I'm running Ubuntu on an older laptop and have read that suspend anf resume should be working fine with APM, which they aren't with ACPI. How should I migrate from ACPI to APM? Do I have to compile a new kernel or can I simply install ampd with dependencies and disable ACPI at boot? How can I chech if APM vs. ACPI is in use?

---

### Post by ranf on 2005-10-20
[QUOTE=posterlu]How can I chech if APM vs. ACPI is in use?[/QUOTE]
Look at the kernel log (in a terminal):
```
less /var/log/messages
```
Then use the `/' key to search for `APM' and/or `ACPI'. `n' jumps to the next occurance.

---

