---
title: "[SOLVED] Change boot order"
date: 2008-09-20
forum: General Help
---

### Post by bruce48 on 2008-09-20
HI, I want to change the boot order of grub and get xp to be 1st. Where do I type in menu.lst command and how do you get to it. Also booting to a live CD how do you mount the partition and edit the menu.lst. I have done some work in the edit part of Grub but may need a longer explanation. Thanks:confused:

---

### Post by howefield on 2008-09-20
You'll find the file in /boot/grub/menu.lst

You get there by going to Applications > Accessories > Terminal and typing

```
sudo gedit /boot/grub/menu.lst
```

But do be careful ;)

You'll want to make a backup copy first

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

---

### Post by sayakb on 2008-09-20
You could either install **startupmanager**:
```
sudo apt-get install startupmanager
```And launch it from System->Administration->Startup-Manager 
Change the **Default operating system**

Otherwise, you could also do it directly by typing the foll at a terminal:
```
sudo gedit /boot/grub/menu.lst
```Now navigate to the section where it says "Other operating systems:"
Cut the 4-5 lines for Windows XP (as far as I remember, cut it till chainloader +1)
Paste the lines above the ubuntu option.
You may comment out the "Other operating systems" by preceding it with a # (hash)

---

### Post by bruce48 on 2008-09-20
Thanks. I installed the start up manager and that worked fine. Thanks for the great help. Bruce

---

### Post by sayakb on 2008-09-20
Glad I could help!
Please mark the thread as solved (Thread tools->Mark thread as solved)

---

