---
title: "Xubuntu 8.10 - screensaver not working"
date: 2008-11-19
forum: General Help
---

### Post by Bruce M. on 2008-11-19
Hi Folks,

Got Xubuntu 8.10 up and running but the screensaver doesn't work. All I get is a black screen.

Some info about my system:

MSI K8N SLI-F 939 NVIDIA nForce4 SLI ATX AMD Motherboard c/w AMD Athlon64 3500+
NVIDIA GeForce 7300 GS card (512MB RAM) and installed the recommended driver (177)

Any ideas as to how to fix this?
It was working fine with Xubuntu 8.04

Just noticed that the timer isn't working either? I set it to 1 minute to test and 10 minutes later - didn't activate.

Thanks.
Bruce

---

### Post by gabril on 2008-12-04
Uppgrade to latest ubuntu and that should fix it! 

else:

$ sudo aptitude install xserver-xorg-driver-nvidia
also google for sli in linux, i can IMAGINE that this might give you several problems?

---

### Post by Bruce M. on 2008-12-04
> **gabril said:**
> Uppgrade to latest ubuntu and that should fix it!

I'm running Xubuntu 8.10

> **gabril said:**
> else:

$ sudo aptitude install xserver-xorg-driver-nvidia
also google for sli in linux, i can IMAGINE that this might give you several problems?

I already have xserver-xorg-driver-nvidia
I'll check out this sli thing.
Thanks.

Bruce


**EDIT:**
I've checked it out and quite frankly I'm lost. The driver version I have (installed via 8.10) is 177.80, but on the Nvidia site I see:

> Linux Display Driver - x86
Version: 171.06.01
Operating System: Linux x86
Release Date: April 18, 2008

as their latest.

Mine "should" work.  :(

CHIMO!
Bruce

---

