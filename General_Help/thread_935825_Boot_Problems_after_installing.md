---
title: "Boot Problems after installing"
date: 2008-10-02
forum: General Help
---

### Post by vastlyl0st on 2008-10-02
I have installed Ubuntu on my laptop, I can boot into the system if i boot off the CD, but if I try to boot without the CD I get the following messages and it wont do anything from there

ACPI:EC:acpi_ec_wait timeout, status=0, expect_event =1
ACPI:EC:Read timeout, command =128

any idea on whats going on?

I've installed over vista, as I dont want a duel boot. 
Laptop is a sony Vaio with 1GB memory, core 2 duel processor and i have used Ubuntu 8.04 32bit

cheers

---

### Post by iponeverything on 2008-10-02
> **vastlyl0st said:**
> I have installed Ubuntu on my laptop, I can boot into the system if i boot off the CD, but if I try to boot without the CD I get the following messages and it wont do anything from there

ACPI:EC:acpi_ec_wait timeout, status=0, expect_event =1
ACPI:EC:Read timeout, command =128

any idea on whats going on?

I've installed over vista, as I dont want a duel boot. 
Laptop is a sony Vaio with 1GB memory, core 2 duel processor and i have used Ubuntu 8.04 32bit

cheers

try booting with the option "acpi=force" on the kernel line in grub.

see:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Ryadt on 2008-10-02
There is a bug report on launchpad regarding this issue.
[https://bugs.edge.launchpad.net/linux/+bug/191137](https://bugs.edge.launchpad.net/linux/+bug/191137)

---

