---
title: "why does my system think I have a dual-core?"
date: 2008-11-26
forum: Hardware
---

### Post by BetterSense on 2008-11-26
I have an Acer Aspire One netbook. With intel Atom. Gnome's System Monitor, top, htop, and kpowersave all think I have two CPUs. Htop's CPU usage meters even individually move back and forth.

Hello? Did I get a preproduction dual-core Atom?

---

### Post by amauk on 2008-11-26
Hyper-threading
[http://en.wikipedia.org/wiki/Hyper-threading]("http://en.wikipedia.org/wiki/Hyper-threading")

Physically it's a single core CPU
but the OS "sees" a dual core because of the CPU hyper-threading

---

### Post by finito on 2008-11-26
I have an Aspire one as well, I have windows installed and it also shows 2 processors.

---

### Post by BetterSense on 2008-11-26
So if I had a quad-core, would ubuntu see all four cores or would it also say I had a dual-core?

My friend has kubuntu 8.04 and he says his system only shows one CPU.

---

### Post by dicecca112 on 2008-11-26
> **BetterSense said:**
> So if I had a quad-core, would ubuntu see all four cores or would it also say I had a dual-core?

My friend has kubuntu 8.04 and he says his system only shows one CPU.

4cores

---

### Post by amauk on 2008-11-26
If you had a quad-core hyperthreaded Intel CPU (which don't exist as far as I'm aware, but just pretend) the OS would see eight cores

hyperthreading is hardware-based multi tasking implemented on certain intel CPU's (as opposed to the software scheduling done in the kernel)

physically, there's X cores
logically, there's 2X cores

if your friend has a single core, and the OS "sees" it as a single core, then it's not got hyperthreading

---

### Post by jespdj on 2008-11-26
> **amauk said:**
> If you had a quad-core hyperthreaded Intel CPU (which don't exist as far as I'm aware, but just pretend) the OS would see eight cores
It does exist - the brand new Intel Core i7 processors have four cores and hyperthreading, so it will look like there are eight cores to the OS.

---

### Post by finito on 2008-11-26
for the curious ones

---

