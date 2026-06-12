---
title: "Compaq F700 (F750) with 8.10"
date: 2008-12-23
forum: Hardware
---

### Post by wd5gnr on 2008-12-23
Had this laptop working pretty well with Hardy (had to always put the MadFi drivers in after each Kernel upgrade, but otherwise no real problems). However I upgraded to 8.10 and that's when the fun started.

With Kernel 2.6.27-9-generic the boot process would hang until you'd press keys or the power switch then it would go a little further and hang some more. So I suspected some ACPI oddness. Sure enough, 2.6.24-22 worked ok. Turns out appending pci=noacpi in the grub menu (/boot/grub/menu.lst) on the kernel line allowed the boot to proceed normally.

So maybe that will help someone else.

The only problem I have now is when I log in from the KDM screen (I use Kubuntu) the screen blacks out until I switch to a console and then back to the GUI and I wind up with the screensaver (set for 15 minutes, mind you) running in a little window. I am going to downgrade the NVidia driver I think and see if that helps that.

Anyway, just thought that might help someone else from having to experiment.

---

