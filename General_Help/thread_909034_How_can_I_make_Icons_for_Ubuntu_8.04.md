---
title: "How can I make Icons for Ubuntu 8.04"
date: 2008-09-03
forum: General Help
---

### Post by G9M29 on 2008-09-03
Hi. 
I was thinkig how can I made icons for my Ubuntu 8.04.
Can someone tall me or linked me to somewhere.

---

### Post by Perfect Storm on 2008-09-03
I guess the easist way is to use a current one and modified with your icons.

To build icons there's inkscape and/or gimp via synaptic.

---

### Post by G9M29 on 2008-09-03
But where can I find icons. 
In ./icons there are just that I add, I want to edit the system based icons ??? like human for example.

---

### Post by irrdev on 2008-09-03
Open up the terminal and type the following command:
> gksudo nautilus
Click enter, and a dialog will come up prompting for your administrative password. After a few seconds, the nautilus file manager will come up as root. Now navigate to the  [COLOR="Blue"]/usr/share/icons[/COLOR] folder. There you will find all the system-installed icons. Since you are running as root, you will have permission to edit/modify/add/delete any of the icons.

---

### Post by Perfect Storm on 2008-09-03
I wouldn't recommend that way. Better to make an icon theme in your ~/.icons (home directory).

Example download an icon theme from gnome-look.org and change them with your icons.

---

