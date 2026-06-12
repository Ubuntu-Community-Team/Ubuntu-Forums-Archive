---
title: "Modules"
date: 2009-12-15
forum: Hardware
---

### Post by RedSingularity on 2009-12-15
Is there any way to know if ubuntu has a required module for hardware that is just NOT being loaded up?

---

### Post by Yellow Pasque on 2009-12-16
Do you know the module name?
I guess you already know about such commands as lshw and lsmod.

What device are you having issues with? (maybe you already have a thread about it?)

---

### Post by RedSingularity on 2009-12-16
Well when i do a "lspci" and it tells me my chipset info for, say, a wireless card, does that mean the modules are installed on my system because the card has been identified?

---

### Post by Yellow Pasque on 2009-12-16
No it means the device is physically present. Post output from:
```
sudo lshw -C network
```

---

### Post by RedSingularity on 2009-12-16
Oh no, i am not having a problem......i was using the network as an example.

---

