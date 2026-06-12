---
title: "How to determine wether problems with agpgart are BIOS related"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by Amon_Re on 2006-01-05
I was wondering if someone inhere knows how to determine wether or not the problem i have with amd64-agp is caused by BIOS or by a driverbug.

I'm using an Asus K8V-S XE motherboard with Via K8T800 chipset, and DRI works with no card whatsoever, tested with the following cards (all AGP):

Ati Rage128
Ati Radeon 9200
Ati Radeon 9700
Nvidia GeForce 4 MX

In all instances the amd64-agp reported an aperture size of 32MB, regardless of BIOS settings.

All cards have problems with DRI, DRI works on the R128, however, is completely unusable, since it renders 1 frame per minute.

Nvidia & Ati drivers cause Xorg to lock up.

Bios is up to date.

Tests done with gentoo & ubuntu, kernels used in gentoo were the following versions:
Gentoo 2.6.12-r9
gentoo 2.6.13-r10
gentoo 2.6.14-r4
gentoo 2.6.14-r5

I already mailed the maintainer from amd64-agp, but no reply yet.

Any suggestions as how to further diagnose the problem and cause are welcome

---

### Post by Amon_Re on 2006-01-05
*bump*

---

### Post by Amon_Re on 2006-01-07
[QUOTE=Amon_Re]*bump*[/QUOTE]

Let's kick this sucker once again....

---

### Post by Amon_Re on 2006-01-12
[QUOTE=Amon_Re]Let's kick this sucker once again....[/QUOTE]

And again, surely *someone* must know how to atleast pinpoint the problem?

---

