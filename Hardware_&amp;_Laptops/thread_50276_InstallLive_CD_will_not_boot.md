---
title: "Install/Live CD will not boot"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by missileboat on 2005-07-19
I recently tried to install Ubuntu 5.04 on my IBM R40e Thinkpad. Every time I attempt to install the OS or even try to run the Live CD, my IBM will start to run through the load processes but in the middle of its loading it freezes. The process it freezes at reads:

ACPI: Processor [CPU] (supports 8 throttling speeds)

I have low-leveled the hard drive and reset the MBR but the issue remains. I have also tried two independent install discs thinking that one may be corrupt but that too lead to a dead end. Has anyone else expericiened this or know what is causing it?

Thanks
missileboat

---

### Post by daenney on 2005-07-20
[QUOTE=missileboat]I recently tried to install Ubuntu 5.04 on my IBM R40e Thinkpad. Every time I attempt to install the OS or even try to run the Live CD, my IBM will start to run through the load processes but in the middle of its loading it freezes. The process it freezes at reads:

ACPI: Processor [CPU] (supports 8 throttling speeds)

I have low-leveled the hard drive and reset the MBR but the issue remains. I have also tried two independent install discs thinking that one may be corrupt but that too lead to a dead end. Has anyone else expericiened this or know what is causing it?

Thanks
missileboat[/QUOTE]

ACPI always creates issues with laptops, it still needs a lot of work under Linux so try and boot with the following options:
noacpi  and noapic

---

### Post by missileboat on 2005-07-20
[QUOTE=daenney]ACPI always creates issues with laptops, it still needs a lot of work under Linux so try and boot with the following options:
noacpi  and noapic[/QUOTE]
 I see. So it is an acpi issue. I did some research and found out that everyone with an R40e Thinkpad has had the same problem. I was able to get it to work by typing "install acpi=off" at the install cd's boot screen. Thanks for the help!

missileboat

---

