---
title: "HP Compaq 6715b - last efforts to make ACPI work"
date: 2009-02-08
forum: Hardware
---

### Post by BB_DaKraxor on 2009-02-08
Hi folks,

I've been an unhappy HP Compaq 6715b owner for more than a year now. Tried lots of distros, currently using Ubuntu. I'm almost satisied, only have one big problem: my system only boots if I pass the acpi=off option to the kernel.
(To be more precise, when ACPI is enabled, disk read/write speed is about 200kB/s, therefore the boot process takes about 20 minutes without loading window manager.)

Now this is unacceptable as most likely you need CPU frequency scaling and suspend support on laptops, right?

Interesting fact: I've managed to get ACPI working on Gentoo linux before. Only on 64-bit though. 64-bit Ubuntu does not work, nor do any other distros. With acpi=off everything works perfectly.

I also tried to compile a custom kernel for Ubuntu - tried to include everything I could remember I included in the Gentoo kernel config, but no luck: with ACPI enabled, I get this freaky message when loading the kernel: ```
Module 'acpi' failed to be added to sysfs, error number -17
The system will be unstable now.
```

Please tell me what information you need to help me, I really need to get this working. Using Windows is not an option!

Thanks in advance!

---

### Post by BB_DaKraxor on 2009-02-09
**Update:** I've downloaded and successfully installed openSUSE 11.1. When booting normally, it fails the same way Ubuntu does, but in "failsafe mode", it works PERFECTLY.

"failsafe mode" means passing these options to the kernel:
```
showopts ide=nodma apm=off noresume edd=off powersaved=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
```

I tried to add these options to the Ubuntu kernel in /boot/grub/menu.lst, but that didn't change anything.

Can you guys help me make Ubuntu work as good as openSUSE and Gentoo does? I'd really like to use Ubuntu as I find it more user-friendly than the other two.

---

### Post by BB_DaKraxor on 2009-02-09
No ideas? :(

---

### Post by BB_DaKraxor on 2009-02-10
Well, I think it's settled then: there is no solution to my problems here, while on openSUSE I don't HAVE any. Even direct rendering works! I've never been able to get direct rendering before!

Guess this means goodbye, Ubuntu.

---

