---
title: "Serious help with HDAPS  (Lenovo T61)"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by truse on 2007-11-05
Hi

I have just installed Ubuntu Gutsy on my  Lenovo T61, and most things seems to work quite well.

Im not a very skilled linux user, so i have a litle trouble understanding what to do when i`m going to install IBMs Active Protection system. Yes, i know there is a few guides on howto do it, but i cant seem to understand it totally.. I was hoping someone could help me.

This is what i have done:

Installed hdaps and hdaps and hdaps-utils.
when i run "sudo modprobe hdaps" i get:
FATAL: Error inserting hdaps (/lib/modules/2.6.22-14-generic/kernel/drivers/hwmon/hdaps.ko): No such device

My kernel is: 2.6.22-14-generic

---

### Post by Shinku's fan on 2007-11-06
(kinda bumping)

I second that... Seems the solution is to use the version included in the tp-smapi module (instructions provided here: [http://www.thinkwiki.org/wiki/Tp_smapi](http://www.thinkwiki.org/wiki/Tp_smapi) ). However, I've not been able to compile it.

---

