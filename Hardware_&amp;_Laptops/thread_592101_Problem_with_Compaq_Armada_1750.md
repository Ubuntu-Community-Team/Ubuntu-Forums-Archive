---
title: "Problem with Compaq Armada 1750"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by pordzio on 2007-10-26
Hi everyone!

I've got a serious problem.

I've upgraded my Xubuntu to Gutsy, and the system isn't booting(not quite).

The deal is: when i was upgrading (in the configuration phase), the power "went out". After reboot i finished configuration with "sudo dpkg --configure -a" and now: With options "vga=791 acpi=force" the 
screen goes blank, hdd is acting, like the system is booting and nothing happens (in my opinion). Without the options the system boots, but i get no VTY's, XFCE is working horribly and my hdd is seen as scsi.

With Feisty i've manged to get almost everything working. The only thing i didn't was the lid switch.

Because the laptop has faulty DSDT i used the "custom" version of it from acpi.sourceforge.net.

To boot the 2.6.20 kernels i used options "vga=791 acpi=force".

The 2.6.22 kernel isn't working with the DSDT and without it it makes the problems

---

