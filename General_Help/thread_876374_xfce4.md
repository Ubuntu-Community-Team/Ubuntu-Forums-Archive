---
title: "xfce4"
date: 2008-07-31
forum: General Help
---

### Post by lsd33 on 2008-07-31
Whenever I log in to xfce4 I must go to 'xfce menu->Settings->Desktop Settings' and click the box which allows xfce4 to manage my desktop, it's only after this that I can see my /home/{username} files on my desktop. My sessions are already being saved, so my question is why is this aspect of my desktop not saved? Its not too urgent of a problem but curiosity got the best of me... how do I fix this?:confused:

---

### Post by spiderbatdad on 2008-07-31
I'm trying out xubuntu right now on a friend's computer. I haven't used it much before now. I'm not having the same issue.

Some settings you might check in Settings Manager: Window Manager is set to "Xfwm4.5-svn" Under the Sessions and Startup menu>>Advanced tab: "Launch Gnome  services at startup" is checked.

---

### Post by mali2297 on 2008-07-31
Do you use Nautilus?

In that case, you will have to stop it taking over the desktop in gconf. 
You can do that in one command from the terminal:
```

gconftool-2 --set --type boolean /apps/nautilus/preferences/show_desktop false

```
You might need to put *sudo* in front of the line.

Also, remember to save the session on logout.

---

