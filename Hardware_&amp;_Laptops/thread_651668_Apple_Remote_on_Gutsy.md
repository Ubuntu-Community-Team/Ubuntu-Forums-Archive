---
title: "Apple Remote on Gutsy?"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by zhimsel on 2007-12-27
Hey Forums...

I just built a new computer (AMD Athlon 64, Radeon X800) and I found an IR reciever in my room. Under further inspection, it turns out to be a receiver to an old IR mouse. It reports itself to be "Fujitsu Component IR USB Mouse" /proc/bus/input/devices shows it as:

```

I: Bus=0003 Vendor=0430 Product=0205 Version=0110
N: Name="Fujitsu Component IR USB Mouse"
P: Phys=usb-0000:00:02.0-3.3/input0
S: Sysfs=/class/input/input11
U: Uniq=
H: Handlers=mouse2 event7 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

Is there any way that I can use this with one of the many Apple Remotes laying around my room? I would really like to use this as makeshift Front Row setup (with Elisa). Anyone have any opinions/help/etc?

---

### Post by tgalati4 on 2007-12-27
lirc.org is a start.

---

### Post by zhimsel on 2007-12-27
> **tgalati4 said:**
> lirc.org is a start.

Cool, Thanks!

I'll check it out and report on how it went when I get the time =]

---

