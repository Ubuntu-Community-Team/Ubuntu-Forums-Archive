---
title: "vm multiple monitors"
date: 2008-06-19
forum: Hardware
---

### Post by Wamoc on 2008-06-19
For work I need to use multiple monitors and I would like to replace my windows install with linux running a vm of xp. My question is: would it be possible to have my virtual machine do multiple monitor support?

---

### Post by sdennie on 2008-06-19
If you are able to span other applications across multiple monitors, a VM should be no different.  The guest VM won't be able to detect the multiple monitors I don't think because the graphics card is virtualized and has no real knowledge of what monitors the host machine is hooked up to.

---

