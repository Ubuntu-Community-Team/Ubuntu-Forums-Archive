---
title: "enabling blacklight Fn + F9 (or F10) on Ubuntu 12.10"
date: 2013-04-09
forum: Hardware
---

### Post by Andreap85 on 2013-04-09
Hi,
 I have a Samsung Chronos s.7 (NP700Z3C-S03DE - [http://www.hardwareschotte.de/preisvergleich/Samsung-700Z3C-S03-NP700Z3C-S03DE-Aluminium-Schwarz-p21627173](http://www.hardwareschotte.de/preisvergleich/Samsung-700Z3C-S03-NP700Z3C-S03DE-Aluminium-Schwarz-p21627173)) and I installed on it the last Ubuntu release 12.04. Then I made the upgrade to the 12.10 release (the release upgrade makes work the right click touchpad, that did't worked in U12.04). 
Everything seems to work fine but the the key function for the keyboard blacklight (Fn + F9 or F10); the light is always on and no way to turn it off or decrese the brightness. 

I look around in the web, posts, forums, blogs, everywhere...... and the main answeres to this issue are:
1) add the "voria" repos. and installing the the samsung-tools, samsung-blacklight, samsung-laptop packages (I can not install the samsung-laptop pack. : package not found?! any idea??)

done, with the exception for the samsung-laptop pack. anyway it does not work

2) modify the grub file in /etc/default/:

(defoult in Ub12.10)                                                                     (one of the options found)
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"    --->      GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="  or GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"

done all the proposed options but no one work after updating grub rebooting the system.  

for what concern the last options (point 2) they always referred to the kernel version (more often 3.2..-...) where, typing uname -r on the terminal,I get kernel = 3.5.0-26-generic. may be this the why this method does not work?

any Idea on how to fix this?
thanks

---

