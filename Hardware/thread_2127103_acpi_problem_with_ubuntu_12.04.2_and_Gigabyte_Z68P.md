---
title: "acpi problem with ubuntu 12.04.2 and Gigabyte Z68P-DS3"
date: 2013-03-19
forum: Hardware
---

### Post by acidrop on 2013-03-19
I have Gigabyte Z68P-DS3 (FE Bios) with Intel(R) Core(TM) i7-2600S CPU.
Ubuntu version 12.04.2 LTS x64 with kernel 3.2.0-39-generic #62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux.

I have several problems with acpi to work correctly. I have tried giving all the kernel parameters for acpi following [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI).
The only option that the computer works correctly is with acpi=off but it does not recognize correctly alla the cpu cores and of course it cannot stanby,poweroff etc.

If i remove acpi=off and boot I can see system that it tries to boot until suddenly it standby and I have to press the power to button  to recover again but unfortunately it stops there.

I am attaching the logs if someone can help.

---

