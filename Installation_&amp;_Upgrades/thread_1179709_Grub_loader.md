---
title: "Grub loader"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by joshh88 on 2009-06-05
I'm trying to add Slitaz to grub but when i put /boot/grub/menu.lst in with root i get access denied. i tried vi /boot/grub/menu.lst but i couldn't figure out what or where i need to add info

---

### Post by tommcd on 2009-06-05
To edit /boot/grub/menu.lst you will need to use sudo. So use:
```
sudo vi /boot/grub/menu.lst
``` 
Ubuntu has other text editors that are easier to use that vi, like nano or gedit. Vi is fine though if you are comfortable with it.  
Just replace vi with nano in the above command to use nano. For graphical programs like gedit you should use **gksudo** instead of sudo, so for gedit:
```
gksudo gedit /boot/grub/menu.lst
```

---

