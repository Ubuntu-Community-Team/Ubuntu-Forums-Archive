---
title: "How to prevent drivers from loading?"
date: 2008-06-20
forum: Hardware
---

### Post by lithium on 2008-06-20
I recently installed hardy on my laptop. Now I'm wondering how to prevent it from loading some driver modules for devices I never use anyway. Those would be:

- LAN (tg3)
- firewire
- parallel port (laptop doesn't even have one)

I tried blacklisting the modules in /etc/modprobe.d/blacklist, but that doesn't work. Any idea?

---

### Post by damis648 on 2008-06-20
Try editing /etc/modules

---

### Post by lithium on 2008-06-20
> **damis648 said:**
> Try editing /etc/modules

I only had fuse, lp and something-2 in there. So this does not help.

---

### Post by damis648 on 2008-06-20
Ok, just was an idea.

---

### Post by lithium on 2008-06-20
Yeah, thanks anyway. Open for other suggestions!

Btw I digged around a bit and found

/etc/udev/rules.d/70-persistent-net.rules

which seems to be used to prepare loading the net devices and is being created by

75-persistent-net-generator.rules

There's also

/etc/udev/rules.d/90-modprobe.rules

which I tried to edit but had no success so far... so, any ideas?

---

