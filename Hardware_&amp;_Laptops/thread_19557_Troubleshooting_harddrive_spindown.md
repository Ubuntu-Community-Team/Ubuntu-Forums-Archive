---
title: "Troubleshooting harddrive spindown"
date: 2005-03-12
forum: Hardware &amp; Laptops
---

### Post by hcf on 2005-03-12
Having succesfully edited my /etc/acpi/power.sh. My disk now spins down and stays down for a couple of minutes. However, trying to track down which processes that cause my disk to spin up again I ran into a problem.

I have tried to follow the provedure discribed here:
[https://www.ubuntulinux.org/wiki/IdleDisk](/https://www.ubuntulinux.org/wiki/IdleDisk)

But I don't get any debugging info using dmesg.

I think the problem is that I'm not able to set:
echo="1">/proc/sys/vm/block_dump

If i check it with cat /proc/sys/vm/block_dump I only get an '0'

Am I doing the right thing here?

---

