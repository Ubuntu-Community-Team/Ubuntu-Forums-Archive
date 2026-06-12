---
title: "hdparm not holding?"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by drpaul on 2008-02-17
Since upgrading from Edgy to Gutsy the -B 254 setting in hdparm.conf isn't there when I inspect the status after booting [shown thru -I].

It must be reset by something else [to 128].

Any ideas how to get back to where I don't get the horrible drive clicking problem?

Thanks

Paul

---

### Post by IcarusR on 2008-02-17
Hi,
Have you tried adding the -B 254 setting to /etc/hdparm.conf & saving the file & rebooting ?

Icarus

---

### Post by drpaul on 2008-02-17
Icarus

The hdparm.conf file had the -B 254 as an uncommented line in the first section. Not knowing if that was sufficient, I added a section for /dev/sda which had that in it.

When I check hdparm after booting the power management is at 128. After running

sudo hdparm -B 254

the power management is at 254.

It seems to stay there, but I haven't checked after unplugging and replugging.

Paul

---

