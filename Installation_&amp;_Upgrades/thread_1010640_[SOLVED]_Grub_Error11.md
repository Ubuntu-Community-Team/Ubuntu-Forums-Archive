---
title: "[SOLVED] Grub Error11"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by Yathi on 2008-12-14
I wanted to change my ubuntu splash screen so i installed the startupmanager. Downloaded a splash screen. N did the required things in the startup manager. then in menu.lst i added vga = 0x0318 in the defoptions line as was instructed in the tutorial. i checked tat using hwinfo.

Then restarted. When shutting down my new splash screen came. But now ubuntu not booting. In the boot menu if i select ubuntu it is giving 

grub error 11 Unrecognised Device String. 

I used to live disk to add an entry for windows n now m in windows. Windows is booting properly. Wat is the problem????

---

### Post by caljohnsmith on 2008-12-14
If you left a space on both sides of the equal sign for "vga = 0x0318", that might be what is causing problems, so you could try:
```
vga=0x0318
```
To try it, next time you reboot, select the Ubuntu entry you want to boot, press "e" to edit it, select the "kernel" line, press "e" to edit it, then make the change as shown above. Press enter to save the change, and finally "b" to boot Ubuntu. See if that gets you any further, or let me know what happens.

---

### Post by Yathi on 2008-12-15
thanks... got it...

---

### Post by Yathi on 2008-12-16
But instead of changing the kernel line. I changed the root line. I replaced f5f5732b-cd42-45e6-ae24-da2ff88054e9 in the root to (hd0,1) where my ubuntu is installed n that did the trick. Thanks a lot for your help. I did not know can edit in the boot screen.

---

### Post by caljohnsmith on 2008-12-16
Glad you figured out the problem; cheers and have fun with Ubuntu. :)

---

