---
title: "Unable to log in Ubuntu all of a sudden"
date: 2008-07-11
forum: General Help
---

### Post by Jaime Paneque-Galvez on 2008-07-11
Hi there!

I have a dual boot in my PC (XP x64 Pro and Ubuntu 8.04) and have been working recently just on XP. Today I wanted to do something on Ubuntu and have been unable to log in. I am sure am entering the right username and password as I always choose the same for both work and home computers. It has not happened to me before and I did not do any major change on the OS the last time I logged in.

Does anyone have any idea what the problem may be? Any help would be much appreciated!!! Thanks in advance.

Jaime

---

### Post by chrisccoulson on 2008-07-11
If you've got no other administrative user on the system, and you need to reset your main users password, then your best option is to boot in to recovery mode to fix it.

In order to boot in to recovery mode, you need to select the recovery mode option in GRUB. To do this, press [ESC] when GRUB loads (you'll be prompted after the BIOS P.O.S.T, just before the Ubuntu loading screen normally appears). The GRUB menu will now appear. Use the arrow keys to select the 'Recovery mode' option (it will normally be the next one down), and press [ENTER]

Once the machine has booted, you will be presented with a menu. Select the 'root shell' option. Once at the shell, do the following:
```
passwd <*user_name*>
```
...where <*user_name*> is your user name. You will be prompted to enter a new password. Once this is done, type:
```
reboot
```

You should now be able to log in again

---

### Post by Jaime Paneque-Galvez on 2008-07-11
Thanks a lot, it worked! :-)

Jaime

---

