---
title: "Ubuntu 9.04 reboot - how-to disable kexec?"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by staticanime on 2009-04-25
Hey, I upgraded to Juanty yesterday, and it's running fine, except for when I reboot. I have a triple-boot system, but now, when I choose reboot, instead of getting my boot loader, Ubuntu use's kexec to warm-reboot itself, thus bypassing my bootloader, and forcing me to shut down to move to another os. Can I just, like, uninstall kexec, or how can I disable this action?

---

### Post by zhangone on 2009-04-28
I got the same problem.
[https://bugs.launchpad.net/ubuntu/+source/kexec-tools/+bug/364889](https://bugs.launchpad.net/ubuntu/+source/kexec-tools/+bug/364889)

---

