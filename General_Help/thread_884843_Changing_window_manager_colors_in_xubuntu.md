---
title: "Changing window manager colors in xubuntu"
date: 2008-08-09
forum: General Help
---

### Post by spoketire on 2008-08-09
I would like to be able to change the color of my window borders in xubuntu. This was really easy to do in regular Ubuntu. All you had to do was click customize in the settings window where you chose the window manager, but I can't find anything like that in xubuntu. Is there something I can install to customize the colors of themes? If I just have to do it manually, then what do I need to change in the theme files to do this?

---

### Post by john.nicholls on 2008-08-10
Have a look at the choices available in Xfce Settings Manager | User Interface Preferences | Themes. As you select each one, the borders will change.

---

### Post by spoketire on 2008-08-11
I can do that, but what I'd like to do is alter a specific theme and change the window border color, since there aren't any presets that I like.  Will I just have to edit one of the theme files to do this?

---

### Post by zami on 2008-09-30
I understand what s/he's asking, because I'm trying to figure out how to do the same thing.

For example, if I select the theme "Clearlooks", instead of that putty-grey background with entry fields, I want a brown background and tan entry fields.  Is this possible, or do I need to find/make an entire new theme to change colors?

Thanks for any help!

-zami

---

### Post by denham2010 on 2008-10-01
hi,

If you installed xubuntu packages on top of an ubuntu install, the gnome theme configuration packages will still be available for you to use. They may not appear in your menu, but you can run them from the command line.

If you have a native xubuntu install, you will need to edit the theme by hand. Open a root version of thunar:
```
sudo thunar /
```
Navigate to /use/share/themes and locate your selected window manager theme. The file you need to edit is inside the xfwm4 folder in the theme.

I'm not on my xubuntu box at the moment to tell you the name of the file or the lines to change, but they are fairly intuative from just reading them.

Remember to make a backup of any files you change so you can revert if something goes awry.

Zami, what you are after is in the gtk theme. Follow the steps above, but open the gtkrc file in the gtk2.0 folder instead of the xfwm4 folder. The settings are widget specific, so your best bet is to google "gtkrc theme tutorial" for a guide on what you needxto change.



Cheers.

---

