---
title: "Sony Laptop hangs with and without -quiet option"
date: 2008-07-04
forum: Hardware
---

### Post by Olnex on 2008-07-04
With -quiet option, my VGN-C25G hangs at:
ACPI: EC: acpi_ec_wait timeout, status=32, expect_event=1
ACPI: EC: read timeout, command=128
This is a known bug, which can be solved by removing -quiet option. However, after removing -quiet, I got this when boot:
[17.896085] ACPI Error(something-0537): Method parse /execution
failed I\_SB_.PCIO.LPCB.EC__._REG](Node f7c4af1, AE_TIME
[17.896783] pnp: PnP ACPI init
... something here ...
[18.450851] ACPI: bus type pnp registered

and the system hangs there, this happens frequently, as a result, I am not able to use my laptop as every time I have to manually shutdown by pressing the power button and hear a big noise, I am sure this is not good for laptop.

I wonder why this bug takes so long and hasn't been fixed yet?

---

