---
title: "Theming issue..."
date: 2008-08-14
forum: General Help
---

### Post by S.A.A on 2008-08-14
When i change the default theme to another, every administrator window "such as synaptic package manager" appears with no theme at all..

is that normal, or i can fix that.

---

### Post by ad_267 on 2008-08-14
I'm not sure what you mean by no theme at all. There should be a theme, but if you have downloaded a non default theme it will be just the default theme.

You can run these commands to link your root themes to your own users so the themes are applied:
```
sudo ln -s /root/.themes /home/your_user_name/.themes
sudo ln -s /root/.icons /home/your_user_name/.icons
```

---

### Post by S.A.A on 2008-08-14
it didn't work..

---

### Post by sayakb on 2008-08-14
Press Alt+F2 and type in : [B]gksudo nautilus
[/B]Now copy the themes from /home/username/.themes folder to /usr/share/themes folder using the root nautilus window. Btw, FYI, the .themes folder is a hidden folder inside your home folder. Press Ctrl+H to reveal it.

---

