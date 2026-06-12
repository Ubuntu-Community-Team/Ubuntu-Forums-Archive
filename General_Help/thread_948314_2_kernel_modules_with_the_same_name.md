---
title: "2 kernel modules with the same name"
date: 2008-10-15
forum: General Help
---

### Post by Hochlehnert on 2008-10-15
Hi,

I have a server with Ubuntu 8.04 Server x86_64 that's using a Chelsio 10GBe card. Some days ago Chelsio released a new driver that works with kernel 2.6.24.
But the standard kernel also ships this module.

The new module installs to a different path than the original one.

Now that I have 2 modules with the same name in different locations I have some questions about that.

Which modules will be loaded during startup?
Which module will be included in initrd?
How can I check which of these modules was loaded (how can I see a path to the module)?

Thanks, Klaus

---

