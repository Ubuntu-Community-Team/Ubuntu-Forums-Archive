---
title: "How would I get to the screen to type irqpoll all_generic_ide"
date: 2008-10-25
forum: General Help
---

### Post by cryticfarm on 2008-10-25
Last time I installed ubuntu, I got and error when I pressed the install screen for Linux where the orange bar keeps going back and forth for 3 minutes and then i got this error. So I had to use this line to make it work. I later removed ubuntu and now I plan on reinstalling on a smaller partition, but I get the same error and I forgot where to put in the line. It's not a command from what I know and tested.
```
irqpoll all_generic_ide
```

---

### Post by cryticfarm on 2008-10-26
Bump?

---

### Post by confused57 on 2008-10-26
Try pressing "F6" at the initial live cd boot screen, then add the boot options to the very end of the boot line, "enter".

Once you install Ubuntu, at the grub boot menu highlight the first Ubuntu entry, press "e", highlight the line with kernel, press "e" again, then add the boot options to the very end of the kernel options line.  Once you boot into Ubuntu, you can make it permanent:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by cryticfarm on 2008-10-26
I don't have a burned cd. I downloaded, mounted, then installed in windows, rebooted wit the windows and ubuntu option. I still need to install.

---

