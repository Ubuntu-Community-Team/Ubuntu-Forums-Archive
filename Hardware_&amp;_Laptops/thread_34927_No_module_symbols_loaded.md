---
title: "No module symbols loaded"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by Xgates on 2005-05-16
In /var/og/messages and syslog I get this message:

No module symbols loaded - kernel modules not enabled.

I recomplied the kernel and this is what I have in it for those options:

# Loadable module support
#
CONFIG_MODULES=y
CONFIG_MODULE_UNLOAD=y
CONFIG_MODULE_FORCE_UNLOAD=y
CONFIG_OBSOLETE_MODPARM=y
# CONFIG_MODVERSIONS is not set
# CONFIG_MODULE_SRCVERSION_ALL is not set
CONFIG_KMOD=y

I dont get why the logs are saying this.

---

### Post by Xgates on 2005-05-17
anyone?

---

