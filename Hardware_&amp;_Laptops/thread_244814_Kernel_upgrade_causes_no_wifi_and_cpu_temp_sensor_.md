---
title: "Kernel upgrade causes no wifi and cpu temp sensor problem"
date: 2006-08-26
forum: Hardware &amp; Laptops
---

### Post by nvllified on 2006-08-26
I've recently installed Ubuntu on my Toshiba Satellite M105-3041 despite the scare of over heating; however, when I upgrade my kernel to 2.6.15-26-686 ubuntu no longer sees the built in wireless.  Another problem, though unrelated, involves temperature sensors.  I haven't been able to find out my processor's temperature using acpi -t or lm-sensor.  At start up I get 'setting sensor limit   Failed' (or something like that)  Id there any way I can fix this problem?  I'd like to know which kernel my processor runs cooler under.

My machine's specs are as follows:

Intel Core Solo 1.87ghz
chipset: 945GM
wireless Intel® PRO/100 VE 10/100Base-TX

Anyhelp would be great! this computer would run flawlessly under ubuntu besides these minor setbacks.

---

### Post by ltmon on 2006-08-27
Your wireless card is probably an Intel ipw3945, and I had the same problem with this one a while back.

The issue is that the card needs a non-free daemon running, called by the program /sbin/iwp3945d-{your kernel version here}, and you don't have it installed for the new kernel.

It's in the linux-restricted-modules package, so first ensure that that package is installed.  You may have to enable the restricted updates repository to get the version you need for the new kernel:

```

deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

```

Make sure you have this line in the file (or something close to it) in your file /etc/apt/sources.list (viewable through Synaptic).  Pay particular attention to whether the "restricted" repository is there.  By default you should have a line with everything you need except "restricted".

As for temperature monitoring, I've had no luck with lm-sensors on my 945 based laptop.  acpi -t does give me one thermal zone however, which is pretty indicative of the overall temperature of the unit.

L.

---

### Post by nvllified on 2006-08-27
So I've installed the restricted modules what do I do from there?

---

### Post by nvllified on 2006-08-27
Actually I found out it just works! Thank you for your help; I would never have figured it out myself

---

### Post by Trenchbroom on 2006-09-13
Had the same problem after upgrading to 686--works!  I did have to go back into Synaptic and install the restricted 686 files, but after a quick reboot all works great.

Thanks!

---

