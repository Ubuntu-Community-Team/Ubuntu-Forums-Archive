---
title: "learning linux systems"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by ayu on 2008-02-15
Hello,

I was going to post this in Beginner's Talk but realized I'm leaning towards the hardware side.  Are there any tutorials or well written and up to date documentation concerning how the modern system interacts with the (peripheral) hardware?  Things such as where the system looks at during boot and how it knows what drivers to load, etc.  I've hacked around with my system trying to get things working, and followed countless and sometimes contradictory advice while doing so.  Or if somebody can point me in the general direction of why, for example, my network and sound do not work unless I suspend and resume.

Thank you very much,
Ayu

---

### Post by 444 on 2008-02-16
Look into the SysV init process. it's those folders like /etc/init.d/ and /etc/rc[number].d/ that control startup.

Suspend and resume is controlled by ACPI, controlled by stuff in the /etc/acpi folder.

---

