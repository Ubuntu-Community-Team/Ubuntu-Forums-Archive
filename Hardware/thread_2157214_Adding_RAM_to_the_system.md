---
title: "Adding RAM to the system"
date: 2013-06-24
forum: Hardware
---

### Post by rva1945 on 2013-06-24
Hi:

I have and old pc running 12.04, the system has 1GB of RAM, if I upgrade it to 4GB, will I have to re-install Ubuntu, or will it automatically benefit from the upgrade?

Thanks

---

### Post by jp734 on 2013-06-24
The question is, are you currently using a 64bit version? If not, then You might have to replace your OS.

---

### Post by rva1945 on 2013-06-24
I'm running 12.04 32bit version, if I want to upgrade to 4GB (not 8GB), do I need to install the 64 bit version? Will Jack, Rakarrack and Guitarix (guitar effects) run on it?

---

### Post by gifford on 2013-06-24
Here is a good article on ram limits and 32 or 64 bit operating systems.
[http://www.zdnet.com/blog/hardware/clearing-up-the-3264-bit-memory-limit-confusion/3124](http://www.zdnet.com/blog/hardware/clearing-up-the-3264-bit-memory-limit-confusion/3124)

As you will read there are other factors to make your selection, seems to favor 64 bit.

---

### Post by rva1945 on 2013-06-24
OK, but my question is not about memory addressing limits, all I want to know is whether it is the same or not to install Ubuntu on a 1GB RAM PC later upgraded to 4GB or installing on a 4GB RAM from the start.

---

### Post by Yellow Pasque on 2013-06-24
It's the same, and no, you don't need to switch to 64-bit.

EDIT: I guess I should note that if you use hibernate, you'll need a larger swap partition.

---

### Post by rva1945 on 2013-06-24
Thanks and no, I don't use hibernate.

---

### Post by sanderj on 2013-06-24
> **rva1945 said:**
> OK, but my question is not about memory addressing limits, all I want to know is whether it is the same or not to install Ubuntu on a 1GB RAM PC later upgraded to 4GB or installing on a 4GB RAM from the start.

Just plug in the 4GB, and your 32-bit Ubuntu will work. Maybe you'll need to install the 32-bit PAE kernel (if it is not installed already) to get the full 4GB (and not 3.2GB) RAM, but that's easy: see [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Just go ahead.

PS:

Easy check to see if your current Ubuntu is PAE enabled:

```
uname -r | grep -i pae
```

output means PAE.

HTH

---

