---
title: "ethernet broken"
date: 2011-08-01
forum: Hardware
---

### Post by NewbuntuUser777 on 2011-08-01
I'm unable to get ethernet working.  It was working, did an install, now it doesn't work.

lspci doesn't show an ethernet controller 
ifconfig shows eth0

My laptop is an HP and the ethernet controller is realtek according to the documentation

---

### Post by karlson on 2011-08-02
> **NewbuntuUser777 said:**
> I'm unable to get ethernet working.  It was working, did an install, now it doesn't work.

lspci doesn't show an ethernet controller 
ifconfig shows eth0

My laptop is an HP and the ethernet controller is realtek according to the documentation

What does lspci show?
Also can you post output of
```

ethtool eth0

```

---

