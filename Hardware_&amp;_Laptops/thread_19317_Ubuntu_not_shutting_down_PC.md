---
title: "Ubuntu not shutting down PC"
date: 2005-03-11
forum: Hardware &amp; Laptops
---

### Post by Thorongil on 2005-03-11
Hello, together,

I am running Ubuntu Warty + backports updates on a Intel RC440BX ("Rochester" was the codename, I think), Kernel 2.6.8 from backports.

I have enabled power management in the BIOS, and when I do shutdown -h now, it will not switch the PC off.

It says "Power down.", but it does nothing except shutting down the HDD....

I had SuSE 9.2 running on the same box, it DID shut down the power....

What can I do? I have not yet tried Hoary, but I will.

I know, there is some kernel config option which enables "Alternate APM power off" or something like that, you know, what is set in the Ubuntu default kernels?

Maybe some kernel dev can consider this problem in the future?

---

### Post by Thorongil on 2005-03-11
Problem solved...call me an idiot, "acpi=force" did the trick....

---

