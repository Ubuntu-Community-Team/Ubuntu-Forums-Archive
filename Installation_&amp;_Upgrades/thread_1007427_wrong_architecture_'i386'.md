---
title: "wrong architecture 'i386'"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by JulesBl on 2008-12-10
Hi

Trying to install several applications on an Intrepid system, the installer says "wrong architecture 'i386'" for all of them.

The System Monitor gives the following info
Release 8.10 (intrepid)
Kernel Linux 2.6.27-9-gerneric
Gnome 2.24.1

Hardware
3.9gb
Processor E2200 2.2GHz

This does not look like a 64bit system so why won't it install i386 apps?
The installation package is gdebi-gtk 0.3.13

If this is a 64bit system how do I find out, will need to re-load a 32bit system.

If it is a 32bit system why won't it install 32bit packages?

Help

Jules

---

### Post by jenkinbr on 2008-12-10
run the code:
```
uname -m
```

and paste the output

edit: I looked [here]("http://processorfinder.intel.com/details.aspx?sSpec=SLA8X"), and your processor is 64 bit, but the code above will tell what version.

---

