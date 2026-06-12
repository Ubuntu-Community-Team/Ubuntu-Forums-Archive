---
title: "SMP clarification"
date: 2009-09-07
forum: Hardware
---

### Post by Tactical Fart on 2009-09-07
I'm a little confused about SMP. When it says "multi-processor support", does it mean more than one physical processor, or multiple cores. I'm using a Core 2 Duo, and gnome-system-monitor sees CPU1 and CPU2 and both are getting a "payload" (can't think of a better term). The documentation said that it might not be enabled depending on the installation medium. If not enabled, then the kernel needs to be recompiled (a process that I'm having trouble with, but I think I've started enough threads). I used the net-installer disk, but since gnome-system-monitor sees both cores, should I even bother?

---

### Post by ddrichardson on 2009-09-07
Two cores are SMP, which documentation are you referring to?

---

### Post by Tactical Fart on 2009-09-07
> **ddrichardson said:**
> Two cores are SMP, which documentation are you referring to?

Here: [https://help.ubuntu.com/9.04/installation-guide/ia64/hardware-supported.html](https://help.ubuntu.com/9.04/installation-guide/ia64/hardware-supported.html)

I googled for "ubuntu enable smp 9.04" and it was the first result.

---

### Post by ddrichardson on 2009-09-07
Ah I see - that page is for [ia64]("http://en.wikipedia.org/wiki/Itanium#Processors") which needs it compiled in. Core 2 Duo is not ia64 it's x86_64 and there's SMP support in that kernel:

[https://help.ubuntu.com/9.04/installation-guide/i386/hardware-supported.html](https://help.ubuntu.com/9.04/installation-guide/i386/hardware-supported.html)

---

### Post by ddrichardson on 2009-09-07
> **Tactical Fart said:**
> I googled for "ubuntu enable smp 9.04" and it was the first result.

It's difficult for us to get around this being returned on a search because it's not necessary to enable it on most architectures. Most people searching that term will want Itanium.

---

### Post by Tactical Fart on 2009-09-07
So SMP was enabled from the start? Oh well Thanks for the help.

---

### Post by ddrichardson on 2009-09-07
Yes :-)

---

