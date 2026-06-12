---
title: "problem booting with SELinux"
date: 2008-07-14
forum: General Help
---

### Post by Farhan on 2008-07-14
installed SELinux using synaptic (package: selinux-basic). it removed AppArmor. then changed from upstart to sysvinit (installed sysvinit and it automatically removed upstart). rebooted the system and it worked fine.

so as the next step, added "selinux=1 enforcing=1" in the Grub kernel options to start with SELinux enabled but the system is not booting. i am getting stuck at the (initramfs) prompt. seems like the kernel is not being able to load? any help anyone?

thanks in advance.

ps. i can boot without any problem when i set **enforcing=0**

---

### Post by Farhan on 2008-07-14
solved using:
1. [https://wiki.ubuntu.com/HardySELinux](https://wiki.ubuntu.com/HardySELinux)
2. [https://help.ubuntu.com/community/SELinux](https://help.ubuntu.com/community/SELinux)
3. [http://wiki.debian.org/SELinux/Setup](http://wiki.debian.org/SELinux/Setup)

no need to remove upstart and install sysvinit on Hardy.

---

