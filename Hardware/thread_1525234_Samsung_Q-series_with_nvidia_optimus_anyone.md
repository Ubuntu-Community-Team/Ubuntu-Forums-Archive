---
title: "Samsung Q-series with nvidia optimus anyone?"
date: 2010-07-06
forum: Hardware
---

### Post by avilella on 2010-07-06
Hi,

Has anyone tried Linux on a Samsunq Q330, Q430 or Q530 with nvidia optimus?

Cheers

---

### Post by dugh on 2010-08-13
The nvidia optimus graphics cards don't currently work in Linux.

---

### Post by Valshar on 2010-10-09
I just got one of these. Haven't installed ubuntu on it yet, has this been solved on 10.10?

---

### Post by avilella on 2010-10-09
> **Valshar said:**
> I just got one of these. Haven't installed ubuntu on it yet, has this been solved on 10.10?

There is a partial solution to manually switch on/off the discrete graphics card, using acpi_call:

[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

---

### Post by Valshar on 2010-10-20
> **avilella said:**
> There is a partial solution to manually switch on/off the discrete graphics card, using acpi_call:

[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

Hey, thanks for the reply. I tried this but it is a little confusing to me. I followed those 3 or 4 steps and then what am I supposed to do really, after installing the script and running ./test_off.sh?

Also, when I did my last boot (guessing it was an update that did it) suddenly the desktop effects are disabled (they worked fine before) and it searches for drivers when I try to enable them. Obviously the drivers it finds are nvidia's which I know will break the system if I install them. This was even before I tried the previous method, by the way.

edit: oh and the script fails all the tests :/

---

