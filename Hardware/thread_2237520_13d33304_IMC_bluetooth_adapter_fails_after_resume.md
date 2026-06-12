---
title: "13d3:3304 IMC bluetooth adapter fails after resume"
date: 2014-08-02
forum: Hardware
---

### Post by akos.maroy on 2014-08-02
I have an Asus UX32LN laptop with an 13d3:3304 IMC Bluetooth adapter. the adapter seems to work fine on a clean boot, but after a suspend / resume cycle it just breaks. the effect is that when one tries to turn on bluetooth, something crashes in the background, and then bluetooth turns off automatically again. or one can't even turn on bluetooth via the bluetooth UI.

I wonder if there is at least a work-around for this in the form of unloading & re-loading the module that takes care of this device? which module would that be?

---

### Post by akos.maroy on 2014-08-02
as for trying to unload the bluetooth module in general and then re-loading, this doesn't even work:

```
$ sudo rmmod -f bluetooth
rmmod: ERROR: ../libkmod/libkmod-module.c:769 kmod_module_remove_module() could not remove 'bluetooth': Resource temporarily unavailable
rmmod: ERROR: could not remove module bluetooth: Resource temporarily unavailable

```

---

