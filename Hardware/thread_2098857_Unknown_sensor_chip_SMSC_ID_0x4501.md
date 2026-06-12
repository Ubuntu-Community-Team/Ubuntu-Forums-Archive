---
title: "Unknown sensor chip SMSC ID 0x4501"
date: 2012-12-27
forum: Hardware
---

### Post by BambooClaw on 2012-12-27
I have a laptop (HP 5310m) released around 2010 and there appears to be no support for the fan/temp sensor chipset.

When I run sensors-detect it comes up with an unknown chip with ID 0x4501.

Does anyone know what this chip is?

If so, is there a module driver being written for it?

Any help appreciated,



Output of sensors-detect:

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x4501
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

---

