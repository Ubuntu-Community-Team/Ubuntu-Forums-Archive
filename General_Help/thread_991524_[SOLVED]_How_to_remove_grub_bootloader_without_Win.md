---
title: "[SOLVED] How to remove grub bootloader without Windows"
date: 2008-11-23
forum: General Help
---

### Post by Chuchaqui on 2008-11-23
I have been switching over to Ubuntu for a while now (two years or so) and I realized that I have almost no use for windows so I uninstalled windows and resized my partitions to make up for the extra space. When I restarted grub started like usual with the windows/ubuntu option. I wanted to get rid of it but I haven't been able to find out a way how. I uninstalled grub but that did nothing.

---

### Post by 73ckn797 on 2008-11-23
Grub is necessary,

You can edit out any Windows references and the system will only have Ubuntu to boot into. Grub will have options for recovery and memory testing which you do not want to delete.

Go to Terminal and enter:

```
gksudo gedit /boot/grub/menu.lst
```

There you can go to the end of the file and delete the Windows loading info.

---

### Post by jimmy the saint on 2008-11-23
Good fast primer on grub.  
[http://www.howtoforge.com/working_with_the_grub_menu](http://www.howtoforge.com/working_with_the_grub_menu)

---

