---
title: "[SOLVED] Lost colors in Gnome Terminal"
date: 2008-11-01
forum: General Help
---

### Post by lifestream on 2008-11-01
Basically the same post as [http://ubuntuforums.org/showthread.php?t=448572](http://ubuntuforums.org/showthread.php?t=448572)

Yesterday I noticed my gnome-terminal is not showing my pretty colors.
The colors are setup in preferences, but no colors show up unless I do 
ls --color=auto
HOWEVER, please also notice that luyza@lifestream is not displayed in color. Absolutely NOTHING is displayed in color, so creating an alias on ls --color=auto is not going to help.

So, I wonder if anyone can help me restore it ^_^; Having the prompt colored helps me control my ADD! :P

---

### Post by geirha on 2008-11-01
Edit ~/.bashrc and see if you find a line like this:
```
#force_color_prompt=yes
```

Remove the # in front of it if its there, save the file and open a new terminal. Does the new terminal get colored prompt?

---

### Post by lifestream on 2008-11-01
Heya, 
I didn't find what you asked me to, but I saw:
# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

So I uncommented it, and now I've got a really colorful terminal!:P

Thank you for the pointer! Now I've got to summon some magic power to tell me why it went bad :P

---

