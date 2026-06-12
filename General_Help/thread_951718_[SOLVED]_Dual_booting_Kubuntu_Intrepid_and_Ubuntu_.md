---
title: "[SOLVED] Dual booting Kubuntu Intrepid and Ubuntu Hardy, using the wrong menu.lst"
date: 2008-10-18
forum: General Help
---

### Post by Gonz_91 on 2008-10-18
So, I recently installed Kubuntu Intrepid on my machine, which was already running Ubuntu Hardy. When I installed kubuntu, in reinstalled GRUB, and started using the menu.lst available at the Kubuntu partition.
So, I want to start using the menu on the other partition, so that I can uninstall Kubuntu when I feel the need. I'm familiar with hand-customizing the menu.lst file.



Thanks in advance ;)

---

### Post by matjaz on 2008-10-18
Hi,
I am having the same problem here (two ubuntus and the wrong menu.lst in use). I am not planning to remove the second ubuntu, so that the isue does not bother me, but anyway:
When i installed windows on another partition (triple boot with 2xubuntu + winXP on another machine), i remember that i had to reinstal grub to boot in ubuntu.
On the grub cd there was an option find an existing menu.lst within some other menus - i think there is one for repairing grub after windows install - and i selected it (booting from grub disc after windows install) so it found my first menu.lst . On that machine i had two ubuntus: first i installed one on sda5 and then after a while another on sda7 partition of the same disc. After the second ubuntu install, i found that i was using the menu.lst from sda7. But after the grub repair i was booting from the menu.lst on sda5 . So there is my advice: If you will ever want to get rid of kubuntu, before you do that make a grub bootable disc. You will find all the instructions for that on the grub site.
After you will uninstall/delete the kubuntu, you will have to boot from grub disc, and that will hopefully restore your menu.
(choose a repair menu option on the disc's boot menu-i think there is one, but I can't remember)

Matjaz

---

### Post by ajgreeny on 2008-10-18
You can probably do it simply by either using the live CD, following the way shown in my attached txt file or maybe even simpler way, by booting into your ubuntu install and running ```
sudo grub-install /dev/sd?
``` The ? will be whichever your ubuntu disk is, probably sda, but make sure you know before you do it.

---

### Post by Gonz_91 on 2008-10-18
```
sudo grub-install /dev/sd?
```


This is pretty much what I was looking for, and it worked, I am now using the right grub menu. Customizing it was a breeze ;)



(ps: I personally rarely use it anymore (text editors rule), but for anyone out there with problems editing menu.lst, I highly recommend QGRUBEditor)

---

