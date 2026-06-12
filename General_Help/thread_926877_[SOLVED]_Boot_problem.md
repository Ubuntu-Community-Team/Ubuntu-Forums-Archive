---
title: "[SOLVED] Boot problem"
date: 2008-09-22
forum: General Help
---

### Post by ^^rac on 2008-09-22
Hi guys!!

I rebooted to Ubuntu today....

It takes me to Busybox v1.1.3 Built in shell

With (initramfs) (at command prompt) I never saw this before?

I tired booting twice, it does not go to the GUI.....

Any ideas?

---

### Post by Monotoko on 2008-09-22
stick your linux live CD in and check the disk (3rd option) if all is well, reinstall

---

### Post by WRDN on 2008-09-22
At the GRUB screen (bootloader that appears on bootup), highlight the entry for Ubuntu, press "e" and then highlight the line starting with the word "kernel /boot/. . .". Now, replace "quiet splash" at the end of the line with "all_generic_ide". Press Enter, then press "b" to boot.
You should now be able to boot properly. To make this change permanent, open the terminal and type:

```
gksudo gedit /boot/grub/menu.lst
```

Replace the words as described above.

---

### Post by ^^rac on 2008-09-22
> **WRDN said:**
> At the GRUB screen (bootloader that appears on bootup), highlight the entry for Ubuntu, press "e" and then highlight the line starting with the word "kernel /boot/. . .". Now, replace "quiet splash" at the end of the line with "all_generic_ide". Press Enter, then press "b" to boot.
You should now be able to boot properly. To make this change permanent, open the terminal and type:

```
gksudo gedit /boot/grub/menu.lst
```

Replace the words as described above.


Thanks guys!!

I pressed alt +ctrl +f1

And saw it says something about a removable disc not been removed properly......

I ran Windows (First) partition......
And just run checdisk....

Rebooted walla!

Thanks for the help tho! :)

---

