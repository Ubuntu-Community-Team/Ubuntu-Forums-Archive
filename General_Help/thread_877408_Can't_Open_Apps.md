---
title: "Can't Open Apps"
date: 2008-08-01
forum: General Help
---

### Post by adog317 on 2008-08-01
Hi, I just installed ubuntu with wubi today and everything was going great. I was setting things up and when I tried opening "Printing", it said it was starting then it just closed. Same thing for Rhythmbox and Add/Remove Programs. If I can't use these apps, I might have to go back to using Windows.

---

### Post by jonian_g on 2008-08-01
Try to run a program from the terminal.
For example open a terminal and type:

```
rhythmbox
```

and paste the output here to see what the problem is.

---

### Post by adog317 on 2008-08-01
Okay, here is what it gave me:

```
(rhythmbox:7698): Rhythmbox-WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault
```

---

### Post by jonian_g on 2008-08-01
Open Synaptic Package Manager (System>Admin) and search the package python-gtk2 and reinstall it.

This usualy hapens when pygtk is not installed properly.

---

### Post by adog317 on 2008-08-01
Okay, I tried that but it gave me this error message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

---

### Post by jonian_g on 2008-08-01
Open a terminal and type:

```
sudo dpkg --configure -a
```

Then open synaptic, click the refresh button and reinstall python-gtk2.

Seems that a system update broke you pygtk because the package installation was interrupted.

---

### Post by jonian_g on 2008-08-01
See if you have any other broken packages (bottom left corner in synaptic there is a button to show the broken packages, if there are any), and fix them so you won't have any more problems.

---

### Post by adog317 on 2008-08-01
Thank you soooooooooo much!!!!!!!!!!!!!

---

