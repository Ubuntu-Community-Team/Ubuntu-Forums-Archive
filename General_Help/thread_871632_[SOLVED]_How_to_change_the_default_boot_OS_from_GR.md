---
title: "[SOLVED] How to change the default boot OS from GRUB?"
date: 2008-07-27
forum: General Help
---

### Post by guss606 on 2008-07-27
Hi all, 
I have 2 hard disks on my desktop, i installed XP first on HD0 and Ubuntu 8.04.1 on HD1, when i boot i got the GRUB menu list, showing the Ubuntu and the other OS's i have. I want to make XP the default as when i boot without choosing anything i want it to boot the XP..
any help please?!

---

### Post by geirha on 2008-07-27
Alt+F2 or in a terminal:
```
gksudo gedit /boot/grub/menu.lst
```

if you move the windows XP section above the line 
```
### BEGIN AUTOMAGIC KERNELS LIST
```
to make it the first choice, it will be the default. It really must be above that comment line, or else it will disappear next time there's a kernel update.

Also, you can change the **default** option from **0** to **saved**. The latter will make the last chosen OS the default next time.

---

### Post by dexter.deepak on 2008-07-27
try this in terminal
```
sudo gedit /boot/grub/menu.lst
```

you can edit 
```
default 0
```
to ```
default n
```

to select (n+1)th boot option.
so to boot the 2nd boot option, try
default 1

---

