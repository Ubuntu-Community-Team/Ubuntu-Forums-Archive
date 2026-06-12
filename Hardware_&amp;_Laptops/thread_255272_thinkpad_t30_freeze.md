---
title: "thinkpad t30 freeze"
date: 2006-09-11
forum: Hardware &amp; Laptops
---

### Post by checkup on 2006-09-11
Hi,

i saw in the archives that some of you have problems with 6.06 LTS freezing on IBM Thinkpad T30. The problem has something to do with the modules.

I wrote a little script to remove some (for me) unneed modules. Since then, the T30 didn't freeze any more (some days now). 
Before that it freezed several times a day.

The modules are:
  
pcmcia_core pcmcia yenta_socket rsrc_nonstatic irda irtty_sir sir_dev nsc_ircc sony_acpi


I don't know exactly which one of them is the problem but it must be one of them for sure!! If you want to you can fiddle that out and reply to this thread. For all the others: Remove all these modules at runtime and bye bye freezing.

---

### Post by daller on 2006-09-11
If you don't mind, please change the title into something like: "HOWTO: Fix Thinkpad t30 freeze"

I came here to help you, bacause the title didn't include "HOWTO:"

---

### Post by sean_worker on 2008-05-11
fyi, to remove the modules:
```
sudo rmmod pcmcia yenta_socket rsrc_nonstatic pcmcia_core irtty_sir sir_dev nsc_ircc irda sony_acpi
```

---

