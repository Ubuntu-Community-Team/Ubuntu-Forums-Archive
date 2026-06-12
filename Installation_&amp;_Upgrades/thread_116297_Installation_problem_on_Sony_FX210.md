---
title: "Installation problem on Sony FX210"
date: 2006-01-12
forum: Installation &amp; Upgrades
---

### Post by sonyfx210user on 2006-01-12
Hi,
I am trying to install Ubuntu 5.1 on Sony Fx210. It just hangs up when trying to load acpi modules. Other messages indicate various solutions. One of them was to turn acpi off. However I did not see any option like acpi=off while installing. 
What is the correct way to do that?
Thanks.

---

### Post by NunoCorreia on 2006-01-12
Instead of just pressing Enter at the initial installer screen, type this:

linux acpi=off

and then hit Enter.

---

### Post by sonyfx210user on 2006-01-13
Thanks that worked!!!!

---

### Post by b33znutz on 2008-05-03
> **sonyfx210user said:**
> Thanks that worked!!!!

> **sonyfx210user said:**
> Hi,
I am trying to install Ubuntu 5.1 on Sony Fx210. It just hangs up when trying to load acpi modules. Other messages indicate various solutions. One of them was to turn acpi off. However I did not see any option like acpi=off while installing. 
What is the correct way to do that?
Thanks.

> **NunoCorreia said:**
> Instead of just pressing Enter at the initial installer screen, type this:

linux acpi=off

and then hit Enter.



HOLY SH@T!!! I AM BRAND NEW TO LINUX AND I HAVE BEEN LOOKING FOR THIS FIX FOR A WEEK. I HAVE SLACKWARE 12.0/12.1, RHEL 5, FEDORA 8, UBUTNU 8.04 LTS DESKTOP AND SERVER, AND ALL OF THEM HAD THE SAME PROB. I'D START INSTALL AND GET STUCK WHEN LOADING "ACPI: XXXXXXX" .. I HAD SEARCHED FORUMS AND GROUPS FOR A WEEK NOW AND IN THAT TIME I HAVE SEEN ALL KINDS OF FIXES/BUS FOR ALL OF THEM BUT TO NO AVAIL! I ALSO HAD SEEN THE SUGGESTION TO "TURN OFF ACPI" BUT DIDNT REALIZE IT WAS SO EASY! THANKS FOR THE TIP NUNOCORREIA!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! I REGISTERED HERE JUST TO SAY THAT!!! I ALSO GAVE NUNOCORREIA THE "REFERAL" DURING MY REGISTERATION!! THANKS AGAIN!!!!!!!!!!!!!!!!! 


-{]b33z[}-

(OH YA, AND I WROTE THIS IN ALL CAPS BECAUSE I AM YELLING FROM MY ROOFTOP!!!!)

---

