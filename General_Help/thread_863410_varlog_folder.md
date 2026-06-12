---
title: "/var/log/ folder?"
date: 2008-07-18
forum: General Help
---

### Post by sugarplumfairy on 2008-07-18
where do i find the /var/log/ folder?
How do i edit code in the folder?

---

### Post by NikoC on 2008-07-18
Open a terminal
cd /var/log

That's it...
I'm not sure what you mean by 'how to edit code'...
If you want to change the contents of a file:
sudo nano filename
or
sudo vi filename
(nano and vi are editors that work in the terminal)

or sudo kwrite filename (if you are using KDE)
or sudo gedit filename (if you are using Gnome)
or sudo mousepad filename (if you are using Xfce)

Hope this helps you out...

Cheers.

---

