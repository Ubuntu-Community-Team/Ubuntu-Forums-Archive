---
title: "wireless HP tx2-1275dx"
date: 2010-09-08
forum: Hardware
---

### Post by katj12480 on 2010-09-08
I have just installed 10.04 on an HP tx2-1257dx. I have made no modifications. The broadcom-sta-common driver is installed but the wireless is disabled and flipping the switch on the laptop has no effect. It works fine in Windows.

---

### Post by Ayuthia on 2010-09-09
If you go into the Terminal and type:
```

lsmod|grep wl

```
Does it return anything?  If it does not, can you also check:
```

modprobe -l|grep wl

```
There should be an entry for something like wl.ko there.  If there isn't, then the bcmwl-kernel-source package was not built for this kernel.

However, if the modprobe does show a wl.ko file and lsmod does not show the module, you will need to check
```

sudo modprobe wl
dmesg

```
to see if there was an error that it ran into.

---

