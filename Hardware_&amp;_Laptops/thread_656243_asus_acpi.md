---
title: "asus_acpi"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by tzg6sa on 2008-01-02
Hi!

My Notebook has some illnes with linux: the special FN key-combinations doesn't work (The FN key is not recognized), it doesn't shut down itself, I have to do it manually, no battery information, no energy saving mode, etc.
I want to load the kernelmodule asus_acpi (because I have an asus notebook and I hope it will help), but I don't know how schould I do it. I tried modprobe asus_acpi, but it failed.

:~$ sudo modprobe asus_acpi
FATAL: Error inserting asus_acpi (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/asus_acpi.ko): No such device

Could you tell me same hints?

Thanks!

---

### Post by BrianElliott0218 on 2008-01-02
Hi,
I'm not positive this will help, but I have found that when I try to put an OS on a laptop it is usually best to load the OS on a standard desktop by putting the mobile HDD on an adapter and installing to that drive by the usual means, and then dropping the HDD back into the laptop.  It has worked for me on three occassions now.  Once with Windows to a laptop that had no way to boot to CD-ROM, and once with Kubuntu to a laptop that I couldn't get the Live CD to boot on at all, and once with a Compact Flash HDD replacement.  In each case, the usual install wouldn't work, but dropping the already loaded OS into the laptop allowed Ubuntu to find and use all the hardware functions.

Worth a try... :KS

Good luck!
~Brian Elliott
[www.flashcow.com](www.flashcow.com)

---

### Post by Namain on 2008-02-13
try running this:
```
sudo modprobe -r asus-laptop
sudo modprobe asus_acpi
```

Sometimes the asus-laptop module will be loaded instead of the asus_acpi module.  The two are very similar, but work in slightly different ways.  Also they conflict with eachother, so you are lot able to have both running at the same time

---

