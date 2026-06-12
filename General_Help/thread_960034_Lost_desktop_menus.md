---
title: "Lost desktop menus"
date: 2008-10-27
forum: General Help
---

### Post by axelsvag on 2008-10-27
I suddenly experienced a new problem at startup. Everything works perfect up to the login. After the system have accepted the user and password I just get the blue background in the xubuntu desktop. The mouse symbol is there but no menus or icons. 
If I go back to the login (alt+ctrl+backspace) I can use sessions with xfce but no recovery mode connected to xfce. If I choose the xfce I just get the blue background without menus again. I can also get the xterm mode and if I start with terminal I can update through the apt-get. But that has not solved the problem. If I try to use the gnome mode I just get the message that something is missing. Is there anyone who can give me some guidance?

---

### Post by john.nicholls on 2008-10-27
The programs that draw what you see on the screen are xfwm4 (window manager), xfce4-panel (panel) and xfdesktop (desktop manager).
Open a terminal with alt-F2 and enter one of those programs. If that does not fix it, try again with the other two. Then when you've got it working properly, save the session.

---

### Post by axelsvag on 2008-10-27
Tank you for your advice. I will try it tomorrow.

---

### Post by axelsvag on 2009-03-03
OK, it took a lot longer and when I tried xfdesktop everything got back and stayed back after reboot. Than you very much for the advice. I wonder why it was lost in the first place.

---

