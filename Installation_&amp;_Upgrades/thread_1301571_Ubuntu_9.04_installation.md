---
title: "Ubuntu 9.04 installation"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by pradyum on 2009-10-26
I am trying to install Ubuntu 9.04 in to a system.. i have instaled nearly 10 but in those 2 showed this problem

when i selected the option install or using live cd its giving raise to a shell environment
its in this way

--------------------------------------------
BusyBox v1.10.2 (Ubuntu1:1)
Enter 'help' for list of commands

(initramfs) 


----------------------------------------------

please help me from this
how can i solve this problem

thanks in advance..

---

### Post by dstew on 2009-10-26
Usually this means the Live CD is not working well with your system hardware. It could be that the Live CD is no good (bad burn), or that the Live CD kernel is not configured properly for your hardware.

To see if the Live CD is any good, try booting it in another computer of a different type. If it doesn't boot, the disk is probably bad. Try to burn another one, but at a slow speed, no more than 4x. Also, check the MD5sum of the .iso to make sure it downloaded OK. See the [Ubuntu Burning ISO How-To]("https://help.ubuntu.com/community/BurningIsoHowto").

If the disk boots fine on other computers, then it is most likely that the problem is the kernel as configured is incompatible with your hardware. You can alter the kernel configuration by adding kernel parameters using F6 at the opening menu. Some kernel parameters that have helped are acpi=off noapic nolapic all_generic_ide. But it is pretty much guesswork. If you just want to install Ubuntu, you should use the [Alternate Install CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"). It installs the same Ubuntu Desktop system as the Live CD, but it uses a text-based installer that works more reliably.

---

