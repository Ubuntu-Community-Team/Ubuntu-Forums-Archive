---
title: "gnome-color-chooser"
date: 2008-10-21
forum: General Help
---

### Post by tsedrey on 2008-10-21
Hi,

I am trying to install gnome-color-chooser for my 8.10 gnome laptop. I have tried both enabling the package in the package manager and compiling it. Both times, I see the option to use it System > Preferences, but everytime I click on it, nothing happens.

Can anyone help me out?

Thanks

---

### Post by loomsen on 2008-10-21
Just type 
```

gnome-color-chooser &

```

into a terminal... Append an & to make it untie from the terminal, so that either one won't close in case you close the other one, and it should appear:

Mine spits out some GtK errors, and then starts up.

Do you have glade installed?

---

### Post by JackTheDipper on 2008-10-22
@tsedrey:
I guess you don't have enough privileges on the file ~/.gtkrc-2.0. GNOME Color Chooser 0.2.3 just outputs this error to the terminal and quits. Version 0.2.4 at least shows a popup message ;-)

@loomsen:
May I ask which GTK+ errors occur?

---

