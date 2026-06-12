---
title: "Pre kernel crash with i945GT + Core Duo T2050"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by bjorn2die on 2007-11-25
I'm having problems installing linux on my new MSI Speedster A4V (MS-9632) i945GT + ICH7R based motherboard, with a Intel Core Duo T2050 CPU.

It crashed imediately after the bootloader, and decomressing the kernel. I've tried FreeBSD and it too crashed on the BXT loader - and the irony of it all is that the machine runs Windows XP.

Is there a Core Duo issue with linux that I have failed to pick up? I've tried various premutations of the BIOS settings peripherals, APIC etc but no luck.

I've tried most recent distros after Ubuntu failed, and a few old 2.4 kernels too - everything is the same. The only output is included below:

```

Int 6: CR2 00000000  err 00000000  EIP c03f75f8  CS 00000060 flags 00010012
Stack: 00000014 00000000 c03e9d83 c03740c5 c03dffe8 c03ea250
```

Any suggestions on how to get this running with Linux?

---

### Post by linux noooob on 2007-11-25
could it be an architecture problem??
or maybe your burner is busted
and does windows still run?

---

### Post by bjorn2die on 2007-11-25
Install medium is good, works on other hardware. Also tried different CDROMs and PXE install, everything failes the same. After the bootloader is finished (Grub/pxelinux.0) it crashes with the same error.

To exlude the Core Due CPU I also tried a Core Solo T1300 and its the exact same thing. 

Windows is still present on the drive, boots and works fine.

---

### Post by linux noooob on 2007-11-25
wow i am out of ideas:confused:

---

### Post by bjorn2die on 2007-11-26
I've managed to get it starting with FreeBSD by using a harddrive with FreeBSD preinstalled, as to avoid the CD loader that crashes. Their mailinglist suggested a faulty diskcontroller, but how can I determine that the controller is faulty when it "works" with some OSes?

Linux crashes even if its preinstalled on the drive, and if its served from PXE, and I'd really like to run both Linux and FreeBSD so I have a SMP box for both.

---

