---
title: "Running command in a certain terminal at startup"
date: 2008-08-22
forum: General Help
---

### Post by twodayslate on 2008-08-22
I would like to run Finch on startup in a desktop terminal named finchConsole. I already know how to get a [terminal on a desktop](http://twodayslate.wordpress.com/2008/08/22/terminal-on-your-desktop/) but I would like to know how to put finch in the terminal without actually typing in "finch". 

Thanks for the help!

---

### Post by Diabolis on 2008-08-22
You can pass a command as a argument to the terminal. Something like this:
**gnome-terminal -x "command"**

To see all the available options:
**gnome-terminal --help**

---

### Post by twodayslate on 2008-08-22
> **Diabolis said:**
> You can pass a command as a argument to the terminal. Something like this:
**gnome-terminal -x "command"**

To see all the available options:
**gnome-terminal --help**Worked like a charm! Thanks!

---

