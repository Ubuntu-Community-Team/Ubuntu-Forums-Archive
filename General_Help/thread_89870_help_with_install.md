---
title: "help with install"
date: 2005-11-13
forum: General Help
---

### Post by hdaddy on 2005-11-13
i am trying to install ubuntu 5.10 on my comp i put the cd in my comp and reboot then win it comes up to boot i press enter it sead uncompressing kernel ok then keeps rebooting and wont work

---

### Post by matthewv on 2005-11-13
So the ubuntu install cd actually boots..?? You get a nice little ubuntu logo?? Then you press enter and the installer says it is uncompressing the kernel, and then... reboots?

---

### Post by codejunkie on 2005-11-13
[quote=hdaddy]i am trying to install ubuntu 5.10 on my comp i put the cd in my comp and reboot then win it comes up to boot i press enter it sead uncompressing kernel ok then keeps rebooting and wont work[/quote] it's probably an acpi issue at the boot prompt enter this command if your using the install cd```
linux acpi=off
```if your using the live cd
```
live acpi=off
```hope this helps.

---

### Post by hdaddy on 2005-11-13
thanks for the help worked good

---

