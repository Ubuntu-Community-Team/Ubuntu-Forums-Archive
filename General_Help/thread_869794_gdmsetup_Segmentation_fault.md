---
title: "gdmsetup Segmentation fault"
date: 2008-07-25
forum: General Help
---

### Post by confy on 2008-07-25
Hello all
I have problem each time when i try to run gdmsetup. It gives me Segmentation fault

```
confy@live:~$ sudo gdmsetup 
[sudo] password for confy: 
Segmentation fault
confy@live:~$ 

```

I tryed to copy /etc/gdm/gdm.conf to gdm.conf-custom but it dosen't help.

I have problem to load into system cause i see logo and inputs on the right of the screen and it should be on the center.  It happen when i update it from 7.10 (login screen not gdm). Gdm stoped working and i don't remember when and why...

Any suggestions?

---

### Post by confy on 2008-07-26
well, i installed kdm instead of gdm but i still get weird "Segmentation fault" error. I notice i'm not first who have this error... Can someone confirm if it is bug or not?
```
confy@live:~$ gdm --version
GDM 2.20.6
confy@live:~$ sudo gdmsetup 
Segmentation fault
confy@live:~$ 

```
please confirm if you have same error, if yes i'll upload it as bug...

---

### Post by Lantius on 2008-08-10
i have the same problem, does anyone know how to solve it?

---

### Post by pauper on 2008-08-10
[http://library.gnome.org/admin/gdm/2.16/gdm.html#troubleshooting](http://library.gnome.org/admin/gdm/2.16/gdm.html#troubleshooting)

Look for any related errors in ~/.xsession-errors

Add these lines to /etc/gdm/gdm.conf-custom in order to make GDM send debugging
information to system logs. Later change it to "false".

[debug]
Enable=true
Gestures=true

---

