---
title: "How do I make the screen dimmer?"
date: 2008-07-15
forum: Hardware
---

### Post by T2manner on 2008-07-15
I can't seem to make it dimmer.
The button combination of Fn+F5 doesn't work like it does on Windows.

---

### Post by alfalfa31 on 2008-07-15
You'll need to be more specific.  I assume you're talking about a laptop, but which one?

---

### Post by T2manner on 2008-07-15
Sony Vaio VGN-NR498E

---

### Post by alfalfa31 on 2008-07-15
Can you run this command and post the output?

```
grep . -r /var/lib/acpi-support/*-*
```

---

### Post by T2manner on 2008-07-16
I will when I get a chance, my Ubuntu won't boot now

---

### Post by SuperSonic4 on 2008-07-16
It generally depends on your graphics card, if it is nvidia you can install nvidia-settings 

```
sudo apt-get install nvidia-settings
```

and then open that up and reduce the brightness (on X screen 0)

---

### Post by T2manner on 2008-07-16
It's Intel graphics

---

### Post by brokenLockpick on 2008-07-16
The lenovo I'm on uses fn+home(brighter) fn+end(dimmer).

Uses an intel mobile 965

---

### Post by T2manner on 2008-07-16
> **alfalfa31 said:**
> Can you run this command and post the output?

```
grep . -r /var/lib/acpi-support/*-*
```

```
/var/lib/acpi-support/bios-version:R2060J9
/var/lib/acpi-support/system-manufacturer:Sony Corporation
/var/lib/acpi-support/system-product-name:VGN-NR498E
/var/lib/acpi-support/system-version:C3LRC5QH

```

---

### Post by alfalfa31 on 2008-07-16
I don't know how comfortable you are with workarounds and such, but you may want to check out this thread.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115525](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/115525)

There are some detailed instructions as well as a decent set of scripts for you to use, should you choose to go that route.

As it is a bug, but with workarounds, You should be able to find a solution you can live with.  The problem is that your hardware is new, and new stuff sometimes takes a bit to make fully functional (the fault of the manufacturers not sharing, not the fault of Linux).

---

