---
title: "Hibernate from live CD?"
date: 2006-01-15
forum: Installation &amp; Upgrades
---

### Post by Adrian on 2006-01-15
I'd like to know if it's possible to hibernate from a live CD, to see if particular hardware support hibernation without having to make an install first. (Of course, a properly sized swap partition must exist).

I did some experimenting earlier today. I was able to write the RAM to my swap partition and hibernate the machine (booted from an Ubuntu live cd) by doing this as root:

```
echo -n "disk" > /sys/power/state

```

However, I didn't mange to wake it up again. I tried this at the boot prompt:
```
live resume=swap:/dev/hda5

```
(where hda5 is the swap partition)
but it doesn't seem to work. The live CD just starts the "installation" just as if nothing has happened.

Any ideas?

---

