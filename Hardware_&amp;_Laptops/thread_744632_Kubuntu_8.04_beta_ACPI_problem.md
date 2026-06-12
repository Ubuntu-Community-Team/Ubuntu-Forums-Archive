---
title: "Kubuntu 8.04 beta ACPI problem"
date: 2008-04-03
forum: Hardware &amp; Laptops
---

### Post by Olnex on 2008-04-03
I installed 8.04beta on my VAIO VGN-C25G, then when I restarted after install I got:
[48.077466] ACPI:EC: acpi_ec_wait timeout,status=0,expect_event=1
[48.077527] ACPI:EC: read timeout,command=128
I tried to boot with acpi=off, it does not work, I tried the livecd, it works OK, then I booted from hard disk, the problem magically disappeared, I'm not sure what's happened, I saw there are a few people have the same problem on VAIO, I'm not sure if it is worth reporting.

---

### Post by Olnex on 2008-04-03
I found the reason. Because when it works OK, I was using battery not AC, when AC is plugged and boot, the problem arises.

---

