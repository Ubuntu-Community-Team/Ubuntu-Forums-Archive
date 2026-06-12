---
title: "IBM Thinkpad T40 issues"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by oomph on 2006-06-19
Hey everyone,

First post here...

So I just installed Kubunto 6.06 for the first time on my laptop.

So far so good, I really like this distro but i need some assistance getting over a hurdle.

First :
When I shut the lid to my laptop and the laptop goes into sleep/hibernate
it won't come back on 100%
I get video display back and mouse movement but I can't seem to click on any icons in KDE.
I did some research and read over the hardware compatibility support for my model.

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM)

It mentions the following:

*Modem untested. For suspend to RAM, needs APM (not ACPI) : add 'apm=on acpi=off nolapic' (without quotes) to kernel options in /boot/grub/menu.lst , add apm to /etc/modules, and add shpchp and pciehp to /etc/hotplug/blacklist. *

I followed the directions and still am experiencing the errors.

Anyone got any advice?

2nd - How do I get my IBM buttons to work?
Volume control/mute etc?
I did an apt-get on all the packages that have "Thinkpad" in the name.

Thanks in advanced for any help.

---

