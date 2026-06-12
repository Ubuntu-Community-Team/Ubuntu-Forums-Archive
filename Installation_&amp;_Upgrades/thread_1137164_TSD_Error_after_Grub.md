---
title: "TSD Error after Grub"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by lewisjd123 on 2009-04-25
Other than a very slow download, my upgrade appeared to go well - except now after Grub I get an "Invalid TSD Data" error message pop up several times - then the boot proceeds normally and everything is OK - any suggestions on how to get rid of the problem?

---

### Post by jimibond283 on 2009-04-26
I'm having the same problem.  I would like to get some info on this as well.  I don't even know what the problem is in the first place.

---

### Post by jimibond283 on 2009-05-07
Any ideas on this?

---

### Post by Guillaume86 on 2009-05-07
Same problem for me, do you have switched to an ext4 partition for your installation? (I did)

edit: It's not the ext4 partition,
Looks like a kernel problem:
from : Throttling submodule of the ACPI processor driver
source: [http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/acpi/processor_throttling.c](http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/acpi/processor_throttling.c)

---

