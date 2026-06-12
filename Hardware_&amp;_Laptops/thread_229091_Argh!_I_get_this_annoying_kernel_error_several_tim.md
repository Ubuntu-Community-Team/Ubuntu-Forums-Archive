---
title: "Argh! I get this annoying kernel error several times a minute"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by mandrakethepenguin on 2006-08-04
Hi all!


     This is an annoyance that pops up in /var/log/kern.log several times a minute (and not just the Linux kernel either, I've had the same problem on the FreeBSD kernel, but not OpenBSD).  The error is as shows```
Aug  3 12:39:22 ubuntu-server kernel: [4295741.768000]     ACPI-0351: *** Error: Looking up [\_TZ_.THRM] in namespace, AE_NOT_FOUND
Aug  3 12:39:22 ubuntu-server kernel: [4295741.768000]     ACPI-0517: *** Error: Method parse/execution failed [\_GPE._L1C] (Node df7aadc0), AE_NOT_FOUND
Aug  3 12:39:22 ubuntu-server kernel: [4295741.768000]     ACPI-0549: *** Error: AE_NOT_FOUND while evaluating method [_L1C] for GPE[ 0]
```
and so on...

I can install a new kernel (I'm thinking 2.4?) if it will fix this problem.
Any help is apreciated.

Thanks

---

### Post by phitoo on 2006-08-04
> **mandrakethepenguin said:**
> Hi all!
     This is an annoyance that pops up in /var/log/kern.log several times a minute (and not just the 
Thanks

I believe this message is related to the ACPI code on your motherboard. It is most likely an error. A minor one, since the board works. 

If you don't mind loosing functions associated to ACPI turning it off will get rid of the message (add acpi=off to your kernel line in /boot/grub/menu.lst). But if everything else works as it should you're probably better off ignoring it.

---

### Post by mandrakethepenguin on 2006-08-06
Thank you so much! You don't know how many forums I posted on, and this is the first straight answer I got.:D

---

