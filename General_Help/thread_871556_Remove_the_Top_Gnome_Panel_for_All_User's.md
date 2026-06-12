---
title: "Remove the Top Gnome Panel for All User's"
date: 2008-07-27
forum: General Help
---

### Post by Benismyhorse on 2008-07-27
Hi, as the title says, is there a way to only remove the top gnome panel for all user's, please help.:confused:
Thanks

---

### Post by SomeGuyDude on 2008-07-27
Your best bet is to run gconf-editor, then go under apps -> panel -> toplevels. There should be one like top_panel_screen0 or something. Set "auto hide size" to 1, and then I suggest a black panel background. You'll never notice it.

---

### Post by Benismyhorse on 2008-07-27
Hi, I just tried your way, but it is for use in a school environment so I don't think it will work, anymore ideas?
Thanks

---

### Post by Mr Flappy on 2008-07-27
To deactivate: 
sudo chmod -x /usr/bin/gnome-panel

To activate (or if an error occurs):
sudo chmod +x /usr/bin/gnome-panel

Notice that alt+F2 to run programs is disabled, you can use gnome-do instead for this.

---

### Post by Benismyhorse on 2008-07-27
Hi, Thanks for the reply but that would take away both top and bottoms panels is there a way to just remove the top for all user's??
Thanks

---

### Post by Benismyhorse on 2008-07-27
Bump

---

