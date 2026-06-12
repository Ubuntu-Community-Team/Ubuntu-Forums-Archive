---
title: "howto force nvidia module to unload?"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by frogotronic on 2007-05-27
Can I add a parameter "--force"  to the following line of my /etc/default/acpi-support file?

```
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="nvidia --force"
```

or should I add the "--force" to the nvidia line in my /etc/modules file?

Thanks,
CH

---

