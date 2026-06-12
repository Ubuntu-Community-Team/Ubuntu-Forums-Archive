---
title: "Ubuntu 14.04.5 LTS Trusty Tahr Release amd64 crashed on Dell Inspiron 15 7000"
date: 2017-02-25
forum: Hardware
---

### Post by jimhce on 2017-02-25
Hi,

I've just installed the Ubuntu 14.04.5 LTS "Trusty Tahr" - Release amd64 on Dell inspiron 15 7000 laptop (Core i7 and GeForce GTX 960M), but it failed to be booted, there are so many errors during the boot process and finally, the kernel was crashed at following error:

Unable to handle kernel paging request of ffffffffa180
INFO: rcu_sched self -detected stall on CPU
NMI Watchdog: Bug: soft lockup - CPU#1 Stuck ofr 22s! [gpu-manager: 944]

It will be wired if Ubuntu cannot support Dell Inspiron 15 7000 hardware as I  have no problems to install and run CentOS 6.8. Any helps of how to fix it will be great appreciate.

Thank you.

---

### Post by QIII on 2017-02-25
Hello!

The first things I always ask are:  Did you confirm the checksum after downloading and did you check the image for defects from the GRUB menu the first time you fired it up?

---

### Post by mörgæs on 2017-02-25
Better to try 16.10 for new hardware. 
Old software on new hardware is bound to give problems.

---

### Post by jimhce on 2017-02-25
> **QIII said:**
> The first things I always ask are:  Did you confirm the checksum after downloading and did you check the image for defects from the GRUB menu the first time you fired it up?

Yes, the checksum was fine, but I cannot check GRUB menu, it installed on a multi os machine where the CentOS is the default boot, but that GRUB is old, does not have image check. I added the Ubuntu 14 to the grub.conf.


[QUOTE=mörgæs] Better to try 16.10 for new hardware. Old software on new hardware is bound to give problems. [/QUOTE]
I'll try the 16.10, the problem is all my programs are built on version 14, may have to migrant to version 16, not quite sure how much different for C++ development environment.

---

