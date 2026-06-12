---
title: "Huawei Matebook D 14&quot; AMD Ryzen5 2500u suffers from random freezes"
date: 2019-02-01
forum: Hardware
---

### Post by jbugella on 2019-02-01
Dear all,


I have recently bought a new Huawei Matebook D 14" AMD Ryzen5 2500u.

I am suffering from random freezes that forces me to hard rebooting it.
I have seen in a couple of forums that the problem is likely related to CPU and its ACPI, but the case is that in Windows 10 it doesn't happen (hmmm).

 For some other laptop brands, they solve it by disabling the CPU Power Management, but the BIOS of this laptop is very limited and this option is not present.

Any help? please? I like the laptop very much apart from this (big) problem.


PS: I have installed Ubuntu 18.04 as dual boot mode, but I don't think it's related.

---

### Post by alexchiu11 on 2019-06-17
Same Laptop and issue and also dual booting. OP, did you get anywhere with this?

I'm using Zorin 15 which is based of ubuntu 18.01. dead freezes seem to happen when I'm programming. i usually have multiple instances of vscode, terminals , spotify and dozen tabs open in firefox. If I can make this stable, i would love to stop using windows 10 entirely....

---

### Post by ajgreeny on 2019-06-17
It's very difficult to help you both without some details of the hardware.

Please show us the output in terminal of command ```
inxi -Fzx
```
You may need to install inxi as I am not sure if it is installed by default, but if so the first command will tell you to do so.
Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. See my signature below for a **How-to**

---

### Post by lammert-nijhof on 2019-06-18
I had some problems with 18.04 too with my Ryzen 3 2200G. Use Ubuntu 19.04 and Linux 5.0 for a Ryzen APU, since they have the latest AMD drivers. You could also wait till the 1st of August, when 18.04.3 will be released with Linux 5.0. Or for the brave install UKUU and upgrade to Linux 5.0 yourself.

---

