---
title: "Revert custom initrd"
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by kashms on 2006-09-05
I'm running an initrd customized with my own DSDT table. After I recently bumped up my ram I started to get errors in dmesg such as:

```
[17180416.104000]     ACPI-0412: *** Error: Handler for [SystemMemory] returned AE_NO_MEMORY
[17180416.104000]     ACPI-0517: *** Error: Method parse/execution failed [\PHSR] (Node dffe6f00), AE_NO_MEMORY
[17180416.104000]     ACPI-0517: *** Error: Method parse/execution failed [\_GPE._L02] (Node dfffeea0), AE_NO_MEMORY
[17180416.104000]     ACPI-0549: *** Error: AE_NO_MEMORY while evaluating method [_L02] for GPE[ 0]
```

I'm pretty sure it is related to my custom initrd and now I want to revert to the original. The question is how I do that, do I use mkinitramfs (used to make the custom initrd) or reinstall something?

---

### Post by mpokrywka on 2006-09-06
In this specific situation:

dpkg-reconfigure linux-image-`uname -r`

will help, with other packages you can always try:

aptitude reinstall *packagename*

Sometimes reinstall won't be fully performed because if you modified some configuration files (in /etc) package manager will try to keep your changes, and will preserve botched configuration file - in that case those files should be deleted manually before reinstall.

---

