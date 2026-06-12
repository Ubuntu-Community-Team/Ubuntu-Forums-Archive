---
title: "Ubuntu Server 23.04 - Cannot access lpt port even with root user"
date: 2023-06-21
forum: Hardware
---

### Post by yevgengrebionkin on 2023-06-21
Hi all!
I need to write to parallel port. 
I tried to access it in different ways:
 - Tried simple C program that is writing to 0x378, but it is erroring out with message "ioperm: Operation not permitted" at the step when ioperm is requesting the permission for 0x378
 - Tried simple echo to /dev/lp0 and /dev/parport0. The first one is getting hang, the second one is throwing error "bash: echo: write error: Invalid argument"

I tried disabling apparmor, same. I even added root to lp group. Same.
I tried all of above with root user as well. Same.

P.S. The parallel port is identified normally. dmesg output:
[   29.001837] parport_pc 00:03: reported by Plug and Play ACPI
[   29.002046] parport0: PC-style at 0x378, irq 5 [PCSPP,TRISTATE]

Can, please, anyone help me with this issue?
Thanks!

---

