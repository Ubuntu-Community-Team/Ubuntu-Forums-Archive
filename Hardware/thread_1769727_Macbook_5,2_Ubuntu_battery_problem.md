---
title: "Macbook 5,2 Ubuntu battery problem"
date: 2011-05-28
forum: Hardware
---

### Post by _Loki_ on 2011-05-28
Hello, I've go 5,2 Macbook & using both OSX & Ubuntu. That was a bitt difficult for me to&#305; install Ubuntu first time. But at the end, I've managed to installed 10.04 - 10.10 & 11.04 without any problem. But When installing, i needed to use acpi=off command. If I don't use it my screen went black.

Anyway, after installed Ubuntu, I've realized my battery doesnt' show. When I try System-Preferences-Power Management-General Always display as icon it only gives me nothing, just "preferences".Also I've realized if my battery offs, it won't sleep.

Ubuntu can't see laptop properties, that's what confuses me. If any help I'll be greatfull.
I've uploaded screenshot that maybe help.

Also I'm wondering "acpi=off" command could made this.


[B]SOLVED: [https://help.ubuntu.com/community/MacBook5-2/Maverick](https://help.ubuntu.com/community/MacBook5-2/Maverick)

I had to use maxcpus=1, acpi=off is wrong for laptops.

[/B]

---

