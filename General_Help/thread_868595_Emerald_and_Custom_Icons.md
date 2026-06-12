---
title: "Emerald and Custom Icons"
date: 2008-07-24
forum: General Help
---

### Post by Death Dream on 2008-07-24
On another distro I used Emerald would change everything from the background color on terminal and the text color and so on to all programs.... but for some reason Emerald is only changing the window boarder and close buttons. I don't know if this is the way it is suppose to work because I was using KDE last time too.

Also, where can I download some Icon's? I'm just a bit confused on what application I am suppose to use to theme my desktop. I got compiz and Emerald running but its not themeing half the things I wanted to theme (Icons and the main stuff within the windows)

I'm new to Ubuntu if you didn't notice by the default wallpapers.

Any help is appreciated.

---

### Post by Cresho on 2008-07-24
GTK is the window manager
emerald and metacity is the border
icons is the icons
cursor is the cursor.

[http://www.gnome-look.org/](http://www.gnome-look.org/)

if you have problems extracting files, just place the
gtk themes and metacity ones in the /home/yourusername/.themes directory and go custom.  for cursor themes, I use the Xsilver which is animated silver cursor.  Looks handsome.  These gets extracted to /home/yourname/.icons

---

### Post by Cresho on 2008-07-24
when you install emerald, it is suppose to start it automatically when you boot.  If not, post here and someone can help or I.

---

### Post by Death Dream on 2008-07-24
GTK-ChTheme? GTK+2.0 Theme Changer within add/remove list?

---

### Post by Alex K. on 2008-07-24
Can someone provide me a link as to how i can obtain emerald and install it? i've tried a few of the tutorials ive found off google none of which have worked for me.

---

### Post by Cresho on 2008-07-24
deathdream, you download the themes.  u use the theme manager to install.  it has an install button next to customize.  after that, you go into customize and choose the theme you want to try.  It is very very easy.  It is a matter of you figuring it out.  after you do, it is like breathing.

for alex, don't hijack the thread.  go to gnome-look.org and use metacity themes.  emerald takes lots of gpu usage s well as cpu in my own opinion.

---

### Post by Death Dream on 2008-07-24
Cresho, I haven't gotten that far I guess, are you talking about inside GTK?

"GTK-ChTheme? GTK+2.0 Theme Changer within add/remove list?" I don't have this app installed yet and was wondering if this was what I needed.

---

### Post by ad_267 on 2008-07-24
> **Alex K. said:**
> Can someone provide me a link as to how i can obtain emerald and install it? i've tried a few of the tutorials ive found off google none of which have worked for me.

Just go applications - accessories - terminal and enter:
```
sudo apt-get install emerald fusion-icon
```

Go to [www.gnome-look.org](www.gnome-look.org) and download an emerald theme.

Go to Applications - Accessories - Compiz fusion icon and then you can right click on the icon to change to emerald. Go to System - Preferences - Emerald Theme Manager to open the theme and enable it. 

To the OP. Emerald only decorates the window. Emerald needs compiz to be running as the window manager. You go to system - preferences - appearance to change gtk themes, icons, metacity themes, fonts and backgrounds.
You can install compizconfig-settings-manager to customize compiz.
Maybe read this: [http://justanothertechblog.blogspot.com/2007/03/quick-guide-on-customizing-ubuntu.html](http://justanothertechblog.blogspot.com/2007/03/quick-guide-on-customizing-ubuntu.html)
and there's a sticky in this forum here: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by Death Dream on 2008-07-24
If GTK does everything, makes me wonder why I even bothered with Emerald.

---

### Post by ad_267 on 2008-07-24
Emerald changes your window decoration, and replaces gtk-window-decorator used by metacity or compiz. Gtk changes the appearnce of scrollbars, buttons, tabs etc in applications. Icon sets are a separate thing again.

The appearance of most things is changed in System - Preferences - Appearance, but because you installed emerald that uses it's own theme manager for configuration.

---

### Post by Death Dream on 2008-07-24
Yeah I think I'm going to uninstall Emerald, I was to use to KDE and though I needed Emerald to do what I wanted.

Thanks everyone for setting me strait on this =D

---

