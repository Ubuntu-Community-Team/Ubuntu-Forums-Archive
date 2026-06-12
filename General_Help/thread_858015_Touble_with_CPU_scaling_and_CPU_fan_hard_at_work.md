---
title: "Touble with CPU scaling and CPU fan hard at work"
date: 2008-07-13
forum: General Help
---

### Post by StianH on 2008-07-13
Allright, this is what is going on. I've got an ASUS Notebook, model PRO31J with a motherboard of make F3Ja. This laptop comes with a lot of extra software for windows, one of which is the CPU/Performance manager, which lets the user switch between different types of profiles. In Windows XP with this software installed, batterylife is around 2,5 hours using wifi, depending on what profile and load running.

With Xubuntu (or any other Ubuntu version, and other Linux distros I've tried) I get 1,5 hours at most. CPU scaling doesn't seem to work as it should, but must say I don't remember how to look for the details on this.

The CPU fan runs constantly, using the governor panel-applet thing I've set it to powersave, but since this is a Centrino Duo processor I suspect that only core is beeing scaled (in Gnome when using the siminal panel-applet I could select which CPU/core to manage, and added one for each, but without the desireable effects though.

The notebook has an ATI graphics card with dedicated memory, the closed source drivers for this that were suggested out of the box as with the other Ubuntus and are installed.

This is a fresh install as of yesterday, and I'm only using Firefox, Pidgin and the terminal and top doesn't suggest there to be any processes using loads of cpu or memory, and everything works just fine, expcept that it's getting really hot and noisy.

Anyone got any ideas of what to do?

---

### Post by jefe on 2008-07-13
Which module have you modprobed? I'm using acpi-cpufreq, for me, it's the best one, working as it should.

---

### Post by StianH on 2008-07-13
> **jefe said:**
> Which module have you modprobed? I'm using acpi-cpufreq, for me, it's the best one, working as it should.

Hmm, I hadn't modprobed any modules, this is out of the box as I said. Tried doing so now, but doesn't seem to do much good.

Running cat /proc/acpi/thermal_zone/THRM/cooling_mode shows "0 - Active; 1 - Passive", which might lead me to believe active cooling for one "CPU" and passive for the other, but since it's one core, it's all active. How can this be changed? (And am I wrong?)

---

### Post by jefe on 2008-07-13
Maybe check which module is loaded, blacklist this one and replace with acpi-cpufreq. Just for test, maybe this will help?

---

### Post by Execute_Method on 2008-07-13
Please Delete this post

---

