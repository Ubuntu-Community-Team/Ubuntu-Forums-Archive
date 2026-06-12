---
title: "Do I ignore the swap drive, dual boot with xp"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by tommynz1975 on 2009-10-26
Hi guys.

I am attempting to install Ubuntu 9.04, I have 8.04 installed dual booted with XP on a nec laptop

My daft question of the day is. do I just select the /sda5 partition and leave Ubuntu to find later on the swap on /sda6

on step 4 I have right clicked and choosen to format the /sda5 partition as ext3 and mount point it /

do I select the swap on /sda6 and tell the system to format this as ext3
so the install can re-setup swap 

OR will the installer see the swap and use it


I am taking screen shots as I go for as many of the 7 install steps that the system lets me, so I can draw back to them on future referance

okay make this two daft questions.
Does the grub Generally fix its self with the new install?

Many Thanks

---

### Post by zvacet on 2009-10-27
Leave swap as it is and Ubuntu will recognize it.

> Does the grub Generally fix its self with the new install?

If you mean add new kernels then yes.

---

### Post by tommynz1975 on 2009-10-29
It worked a charm thank you..  and so fast to boot.

---

