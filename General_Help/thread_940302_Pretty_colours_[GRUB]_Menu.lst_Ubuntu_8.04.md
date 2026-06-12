---
title: "Pretty colours [GRUB] Menu.lst Ubuntu 8.04"
date: 2008-10-06
forum: General Help
---

### Post by johncp1962 on 2008-10-06
I can't seem to get the pretty colours feature to work. Here is the appropriate section of my menu.lst:


# Pretty colours
color green/black red/black

I've searched the web extensively on this and it seems like a simple change; so either I'm doing something incorrectly or this feature isn't functioning properly in 8.04.

Thanks for listening.

John

---

### Post by drs305 on 2008-10-06
Try doing it with Startup-Manager. At least you will know it's not a syntax error. 

Install:
```
sudo apt-get install startupmanager
```

Run:
System, Administration, StartUp-Manager > Appearance. Boot loader menu colors.

---

### Post by johncp1962 on 2008-10-06
Thank you for that. Still the same results. Perhaps I'm not understanding what is supposed to happen. The colors show *only* on the bootloader menu (i.e. the portion where the kernel is chosen, if necessary), but colors cease to show during the remainder of the boot process. Am I missing something?

John

---

### Post by jerome1232 on 2008-10-06
That is actually how it functions, srry.

---

