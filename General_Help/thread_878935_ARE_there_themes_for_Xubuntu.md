---
title: "ARE there themes for Xubuntu?"
date: 2008-08-03
forum: General Help
---

### Post by Thecoolguru on 2008-08-03
I can't figure out how to do anything pretty with themes, compiz, etc. I'm running Xubuntu 8.04. I'm really confused...

---

### Post by jolx on 2008-08-03
well there are themes on [gnome-look]("http://www.gnome-look.org/index.php?xcontentmode=100")

but what exactly are u confused about?

---

### Post by T2manner on 2008-08-03
Gnome Look is themes for Gnome DE.
He's using Xfce.
You can find a lot of stuff for Xfce [here]("http://www.xfce-look.org/"), including themes.

---

### Post by jolx on 2008-08-03
> **T2manner said:**
> Gnome Look is themes for Gnome DE.
He's using Xfce.
You can find a lot of stuff for Xfce [here]("http://www.xfce-look.org/"), including themes.

cool

but the gtk2 themes are the same so they can be installed on either xfce, gnome, lxde or anything that uses gtk2

---

### Post by Thecoolguru on 2008-08-03
Ok say I downloaded my theme, but I can't figure out what to do with it! The instructions to put it in the /home/.theme file, but I can't find it. Also, Xubuntu doesn't have a System menu. Is that supposed to happen?

---

### Post by sub2007 on 2008-08-03
.themes is hidden - you need to show hidden files with CTRL+H.

Settings for Xfce are in the Xfce Main Menu and can be found in either the settings and system menus (settings usually for Xfce based stuff, system for system based stuff). For themes click Xfce menu > Settings > User Interface settings.

Alternatively you can extract it to /usr/share/themes (needs root access) which will  allow your themes to be used by all users on your system.

Finally for Compiz, assuming you already have installed it then you will need to install ccsm (sudo apt-get install ccsm) and then access the Compiz settings from Xfce menu > Settings > Advanced Desktop Settings.

---

### Post by Thecoolguru on 2008-08-03
It won't let me extract it to /usr/share/themes

What do you mean by root access? I'm afraid I'm a tad rusty on my Linux...

---

### Post by sub2007 on 2008-08-03
/usr is a protected folder and you must be a superuser to add files to it. In Ubuntu you get superuser access by using the sudo command (or gksu which is a graphical way).

To open it as superuser enter in terminal:

```
gksu thunar /usr/share/themes
```

and enter your password when you are prompted. That will open a thunar window that you can add the theme to. I would extract the theme to the Desktop (or wherever) and then just drag and drop into that folder. Be careful with that window and **close it when you are done with it** because it is a root file manager which means you CAN delete anything and it won't care.

PS: using a root file manager is very powerful but should only be used where absolutely necessary. Never open one unless you absolutely need one and only use it for what you need it for.

---

### Post by Thecoolguru on 2008-08-03
It's now in the themes folder, but how the heck do I use it??

---

### Post by Thecoolguru on 2008-08-03
argh it says i'm using the theme but neither of my themes look at all like what they are supposed to...

---

### Post by zirrush on 2008-08-04
> **Thecoolguru said:**
> argh it says i'm using the theme but neither of my themes look at all like what they are supposed to...

Just a quick explanation... your GTK2 themes are your actual menu, background, and window colors.  The XFCE (xfwm) themes are your window manager themes, which is your window titles and border. So, keep this in mind when downloading themes for xfce.  Some themes will have both a gtk2 and xfwm4 theme, while others may only contain one of the two.

Xfce Settings Manager:
User Interface = GTK2 themes and icon sets
Window Manager = Xfwm themes (xfce themes)

Window Manager Tweaks also has transparency effects under the composition tab.


To install gtk2 or xfwm themes, you can extract the files to the .themes folder in your home directory. As for icon sets, extract the files to /usr/share/icons


Remember that in *nix any files or directories beginning with a period are hidden.  In order to see hidden files, enable showing of hidden files from your file manager (ctrl+h in thunar) or from the terminal you can do: ```
ls -a
```


Other commands you might find usefull are:
```
man man
man sudo
```

---

