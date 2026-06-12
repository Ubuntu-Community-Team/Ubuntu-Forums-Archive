---
title: "Intel_Idle driver: is it working on your system ?"
date: 2011-02-23
forum: Hardware
---

### Post by dino99 on 2011-02-23
If your system use an Intel hardware, can you check if it work:

into a terminal, run:
- dmesg | grep "intel_idle"
- uname -a

then please report and add "affect me too" to bug 684888 if the first command return:

intel_idle: does not run on family x model xx

---

### Post by fjgaude on 2011-02-23
Well, I seem to have the **idle** okay or am I missing something:

```
frank@cutie:~$ dmesg | grep "intel_idle"
[    0.870421] intel_idle: MWAIT substates: 0x1120
[    0.870423] intel_idle: v0.4 model 0x25
[    0.870423] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.870689] ACPI: acpi_idle yielding to intel_idle
```

Notice my signature.

---

### Post by dino99 on 2011-02-24
> **fjgaude said:**
> Well, I seem to have the **idle** okay or am I missing something:

```
frank@cutie:~$ dmesg | grep "intel_idle"
[    0.870421] intel_idle: MWAIT substates: 0x1120
[    0.870423] intel_idle: v0.4 model 0x25
[    0.870423] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.870689] ACPI: acpi_idle yielding to intel_idle
```

Notice my signature.

no issue for you :)

---

