---
title: "HDD migration altered boot screen"
date: 2008-10-28
forum: General Help
---

### Post by attercop on 2008-10-28
Just upgraded to a bigger faster hard drive. Copied everything across using the dd command. Everything works and boots as it should, except now the normal progress bar on boot is now text. Does anyone know how i can get it back to a bar?

Using fully up to date Hardy.

---

### Post by logos34 on 2008-10-29
try:

System>admin>startup-manager>boot options tab>**uncheck** "Show text during boot" box

---

### Post by attercop on 2008-10-29
Thanks for replying. That hasn't done the trick unfortunately. I've also tried reinstalling usplash and usplash-theme-ubuntu but that hasn't done it either. When i start startupmanager i get this:

```
andy@andy-desktop:~$ sudo startupmanager
[sudo] password for andy: 
Grub2 not detected
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Grub Legacy detected
Usplash detected
Splashy not detected
```

---

### Post by logos34 on 2008-10-29
the 'kernel' line in menu.lst should have 'quiet' option.  Not sure what else to suggest

---

### Post by attercop on 2008-10-30
Yeah it has "ro splash clocksource=acpi_pm vga=792 quiet" options after the uuid.

Copying everything over using dd must have screwed something. No matter, i'll reinstall with the new 8.10 in the next week or two.

---

