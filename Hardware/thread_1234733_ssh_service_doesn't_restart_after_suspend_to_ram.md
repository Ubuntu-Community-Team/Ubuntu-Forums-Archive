---
title: "ssh service doesn't restart after suspend to ram"
date: 2009-08-08
forum: Hardware
---

### Post by pseudonym on 2009-08-08
Tried editing /etc/default/acpi-support like so -
```
# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="ssh"
```
Which you might think should work, but no.

Any other ideas?

TIA

---

### Post by pseudonym on 2009-08-12
bump

---

