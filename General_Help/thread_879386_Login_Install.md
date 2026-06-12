---
title: "Login Install"
date: 2008-08-04
forum: General Help
---

### Post by pat_riedacher on 2008-08-04
ok long story short i was sissy and uninstalled the login application for kde could some please post the comand i'll need to install it again and getting it to work.

also help trying to get the gnome login to work instead of kde would be useful but i want linux to be working before a change anything else

---

### Post by mdsharp24 on 2008-08-04
Not sure I understand what it is that you did, but you could always boot to single user mode / recovery mode and apt-get install whatever you deleted.

---

### Post by loboc on 2008-08-04
```
sudo apt-get install kdm
``` 

or

```
sudo apt-get install gdm
```

```
sudo dpkg-reconfigure gdm
``` to switch between the two

I think gdm is better kdm crashed on a few themes i downloaded from kde-looks.org, might have been poor theme writing though

---

### Post by loboc on 2008-08-04
CTRL+ALT+F1 will get you to a tty prompt if your are staring at a blank screen

---

### Post by pat_riedacher on 2008-08-04
thanks loboc thats exactly what i needed i think 
i had gdm to start with i liked it better anyway

---

