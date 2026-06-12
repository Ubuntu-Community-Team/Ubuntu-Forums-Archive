---
title: "Virtualbox installation 8.04 crashes"
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by worksofcraft on 2009-02-14
[    15.621716] Kernel panic - not syncing: Attempted to kill init!

Im'running Virtualbox on Ubuntu 8.04 host and that's what I get trying to install the very same version as a guest on a virtual machine!

I tried it on virtualbox with a win XP host too... same result :(

Note: I've had no problems installing 8.10 or Windows XP guests... any ideas what is going wrong with Ubuntu 8.04?

---

### Post by tedjordan on 2009-09-20
I am running version 3.0.6 and had the same problem.

I went under "system" settings and clicked on both
ACPI options.  I believe that was it, altho I did turn
on more of the CPU settings too.

good luck
funutation

---

### Post by worksofcraft on 2009-12-17
Thanks, yes Enabling the ACPI and IO APCI on the virtual box motherboard solves the problem.

Processor PAE/NX was not necessary and neither were the processor acceleration options. The later would seem a good idea if the host processor supports them.

Thanks for solving this problem for me and sorry I didn't respond sooner.

---

### Post by granade on 2010-07-11
This is also true with VB 3.1.8.

Was testing remastersys of Ubuntu 8.04.


Thanks!!:D

---

### Post by A4driano on 2012-07-26
Thanks. I downloaded Ubuntu 8,04 to install it on Virtualbox in order to learn with a tutorial. It works.

---

