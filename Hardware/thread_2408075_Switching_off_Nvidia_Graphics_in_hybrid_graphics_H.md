---
title: "Switching off Nvidia Graphics in hybrid graphics HP Zbook G4"
date: 2018-12-13
forum: Hardware
---

### Post by adunatioastralis on 2018-12-13
**Background:**

I [posted previously]("https://ubuntuforums.org/showthread.php?t=2401463&p=13801833#post13801833") regarding an issue I was having in terms of getting Ubuntu to run on this laptop (Zbook G3 owners, this also applies to you), without setting the BIOS to 'discrete graphics'.

Eventually I was able to solve this problem by applying the following kernel parameters "[FONT=gotham]pcie_port_pm=off acpi_osi=Linux acpi_rev_override=5" in the grub configuration file.

**Problem:**

However, **when using either the Prime Indicator Plus GUI or "cat /proc/acpi/bbswitch" (I installed bumblebee following [this]("https://www.youtube.com/watch?v=5nGbWE-pvIE") guide), I can see that the laptops Nvidia GPU is still not properly powered off**, as it states 'NVIDIA GPU is powered ON' and, sadly, this is still reflected in battery life. There is a 'force NVIDIA GPU to power OFF' option in the Prime Indicator Plus dropdown, but selecting it seems to have no effect at all :mad:

What steps may I take to shut it off properly (and safely)?
[/FONT]

---

