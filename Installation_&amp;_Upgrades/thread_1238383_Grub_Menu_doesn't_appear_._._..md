---
title: "Grub Menu doesn't appear . . ."
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by bhendry on 2009-08-12
I just installed kubuntu to my new pc.  It goes through the installation process until reboot.  When it reboots, there is no Grub menu - only the old Windows boot.ini offering Windows XP or the recovery console.  Kubuntu went onto a new hard drive that had not previously been formatted. How do I get to the menu.lst??

thanks!  

Bob Hendry

---

### Post by Soul-Sing on 2009-08-12
```
gksudo kate /boot/grub/menu.lst
```

---

### Post by bhendry on 2009-08-13
Thanks - let me rephrase my question.  When my pc starts, it boots directly into the windows (XP) boot.ini offering me a choice of Win XP Professional or the Windows Recover Counsole.  No option to boot into Kubuntu.  How do I get to that "grub' menu from a cold reboot?

Thanks.

---

