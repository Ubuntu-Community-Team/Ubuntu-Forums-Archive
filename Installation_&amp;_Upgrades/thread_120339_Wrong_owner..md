---
title: "Wrong owner."
date: 2006-01-21
forum: Installation &amp; Upgrades
---

### Post by Balder on 2006-01-21
Hi!

Hope this is the right place... 

I have just installed Ubuntu. On the harddisk was already Windows XP, so at the end of the Ubuntu installation I accepted the GRUB bootmanager and now Ubuntu starts first. That would have been fine had I been the only user, but since I do'nt want to see the wife too confused (she does'nt even know the existence of Ubuntu) it would be nice to have XP to start automatically instead. And then, as a second choise, Ubuntu.

I know (or at least think I know) how to do it in; grub->menu.1st, but apparently I am not the right "owner" and wo'nt be allowed to edit, default 0 to default X_sequence.

Does anyone know how to change "ownership"?

---

### Post by adwait on 2006-01-21
Use sudo:

```
sudo gedit /boot/grub/menu.lst
```

When it prompts you for your password, enter your normal user password.

---

### Post by Balder on 2006-01-21
Thanks for the quick answer. I wrote; sudo gedit /boot... etc. plus my password in a terminal. That opened an empty; menu.1st (/boot/grub) - gedit.

What do I do next? :confused:

---

### Post by kosmic on 2006-01-21
and empty terminal ??
 
type this in a termnial
 
[LEFT]sudo gedit /boot/grub/menu.lst (it is an L lowercase lst)
 
then it should open Gedit it a lot of text just find the correct one and change :) if you need more help, post where the content os the menu.lst, because i'm not in home rigth now :([/LEFT]

---

### Post by aysiu on 2006-01-21
[QUOTE=Balder]Thanks for the quick answer. I wrote; sudo gedit /boot... etc. plus my password in a terminal. That opened an empty; menu.1st (/boot/grub) - gedit.

What do I do next? :confused:[/QUOTE] It looks as if you wrote a menu.**1st** (first) instead of menu.lst (**LST**). Try copying and pasting the instruction instead of re-typing it. Paste is shift-insert.

---

### Post by Balder on 2006-01-21
Sorry folks. I do'nt catch the point but thank you anyway for trying.

---

### Post by Balder on 2006-01-21
[QUOTE=aysiu]It looks as if you wrote a menu.**1st** (first) instead of menu.lst (**LST**). Try copying and pasting the instruction instead of re-typing it. Paste is shift-insert.[/QUOTE]

Exactly! After a few minutes of "heavy thinking" I managed to do it right. Thank you all for helping. Ever so happy now. This is a great forum. :D

---

