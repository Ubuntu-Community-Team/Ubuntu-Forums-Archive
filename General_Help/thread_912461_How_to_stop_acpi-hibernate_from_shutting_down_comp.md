---
title: "How to stop acpi-hibernate from shutting down computer."
date: 2008-09-06
forum: General Help
---

### Post by mempman on 2008-09-06
When I select to hibernate my hp dv2000 laptop, the system goes through a shutdown instead of actually hibernating.  Thus when I turn the system on, it does a fresh bootup.


I think this problem might be related with a setting in /etc/default/acpi-support file.  Here is an exert that I believe is responsible for this problem:


> 
# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=platform


I think the problem is that the variable HIBERNATE_MODE is set to platform.  I just want to know what other value I can change this to?

---

### Post by niccholaspage on 2008-09-06
I have Bigger problems with hibernate.And my acpi-support file is this:
```
# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown
```

---

### Post by Predator106 on 2008-09-06
Mine's the same as above, my hibernate works fine, so does suspend.

---

