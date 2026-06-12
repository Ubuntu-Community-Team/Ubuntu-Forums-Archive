---
title: "[SOLVED] Help!!!!!!"
date: 2008-08-02
forum: General Help
---

### Post by robotman5 on 2008-08-02
i was trying to Install Ubuntu on my Maxtor Harddrive but it didnt work i got this black screen with a X Cursor thats it so i just restart the pc (and take the cd out) i get Error 21

and i try to install Ubuntu again and i get LOTS of Errors to much errors i cant even type here!:(:(:(


Someone Please Help !:(



Note: i am on my parents Windows XP PC

does ubuntu have issues with Maxtor Hard-Drives?

---

### Post by tamoneya on 2008-08-02
the hard drive manufacturer is most likely not the problem.  Ubuntu would only really have a problem with the hard drive if it was failing in which case XP would be broken as well.  Error 21 is most likely a GRUB error.  Can you boot from the liveCD again and post the contents of /menu/grub/menu.lst  Also the strange cursor and the black screen are most likely a result of improper graphics drivers.  Do you know what your graphics card manufacturer is.

---

### Post by robotman5 on 2008-08-02
:( My Graphics card of is this ATI Radeon 9250


and besides i formatted my Windows XP (im not sure my dad did that)


Plus its not the live-CD:(

---

### Post by tamoneya on 2008-08-02
how did you install it then without the liveCD and with a formated XP.

---

### Post by robotman5 on 2008-08-02
it didnt say Live-Cd on the Install Screen

---

### Post by lisati on 2008-08-02
> **robotman5 said:**
> it didnt say Live-Cd on the Install Screen
If you ended up with a graphical interface when booting from the CD it probably was the Live CD.

---

### Post by thegodfaza on 2008-08-02
BTW, making "HELP" as your title usually won't get you any. Putting your problem in the title will.

---

### Post by tamoneya on 2008-08-02
That seems like the live CD to me.  Can you run it and get to the graphical environment.  Then browse to /boot/grub/menu.lst of your hald installed ubuntu.

---

### Post by robotman5 on 2008-08-03
Never-Mind my dad found out it was the CD


so  we burnt another CD and it worked!

---

