---
title: "ACPI on laptops"
date: 2005-11-12
forum: Hardware &amp; Laptops
---

### Post by linuxfj on 2005-11-12
I have loaded Ubuntu 5.10 on a Acer Travelmate 4602WLMi. I had Fedora Core 4 before. Once again, the battery monitor is not working, also it does not detect if the laptop is offline or not.

Now, there are a lot of complaints regarding this issue and a lot of suggestions how to resolve this. With Fedora I had to do too much searching to try to get things to work!

My question is, is ACPI so difficult that it does not work? Or is ACPI very low on the priority list? I expect a solution from Ubuntu, not some other linux fundi who has the time and knowledge to fix it.

ACPI is fundamental to laptops and I am trying my best to spread the Linux message as I am a loner amongst all the Windows users. These fundamental issues that does not work, does not help my crusade.

---

### Post by 23meg on 2005-11-12
ACPI support has to do with the kernel rather than your choice of distro and if you're using the same (or similarly dated) kernel version in more than one distro it's natural that it won't work with any of them. Your best bet is to recompile your kernel with ACPI support for your chipset, which should be well documented if you do a search on the web.

---

### Post by linuxfj on 2005-11-12
If we want Linux to succeed, we cannot expect each and every user to go and recompile his/her kernel just to get ACPI to work properly. That is just plain nonsense.  Just look at the threads after this one regarding ACPI!

I repeat, ACPI is a fundamental part of most laptops  or am I wrong? For the ordinary user like me, it should just work.

---

### Post by linuxfj on 2005-11-12
I just searched Bugzilla with the ACPI keyword. My disappointment starts to grow......

---

