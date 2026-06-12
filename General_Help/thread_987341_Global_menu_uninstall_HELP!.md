---
title: "Global menu uninstall HELP!"
date: 2008-11-19
forum: General Help
---

### Post by kitsune ravo on 2008-11-19
Need help, now!

Here's the deal: I thought that making my Linux computer look like a Mac for a while would be fun. So I did. And it was. That is, until I wanted to go back.

I Installed Global menu using the commands in the first post of this link: 
[http://ubuntuforums.org/showthread.php?t=241868&page=224](http://ubuntuforums.org/showthread.php?t=241868&page=224)

It worked until I wanted to get rid of it. I remove it from the panel, but my apps still don't have menus. I've looked in the package manager, it isn't listed. I've tried stuff like "sudo apt-get remove gnome2-globalmenu applet" and "sudo apt-get clean && sudo apt-get update && sudo apt-get install --reinstall -y libgtk2.0-0", and I've even gone so far as to remove my .gnomerc file and other gnome setting, but like a virus, this program will not give my menus back.

I need help really bad. Please, anybody who knows how to fix this without a reinstall, help me...

Edit: Solved by cIIIz on post #9. Thank you!

---

### Post by kitsune ravo on 2008-11-20
Sorry to bump this, but it's now on the fourth page with 16 views, so I have too. I really need my menus back! Most of the stuff on my computer is ether hard to use or completely unusable without menus!

---

### Post by eternalnewbee on 2008-11-20
I found this link. Hope it helps you:
[https://wiki.kubuntu.org/global_menu](https://wiki.kubuntu.org/global_menu)

---

### Post by kitsune ravo on 2008-11-20
I had already seen that link (for Ubuntu, but the Kubuntu one reads the same as the Ubuntu one...)

In case anybody wants to know how I solved this, I never did. I backed up my home folder and reinstalled. I had hoped never to encounter a virus for Linux. After four years, that hope has been ruined. The last virus I got on windows look like a cool program but took down my computer. Global menu looked like a cool program but took down my computer.

Then again, I had installed and used it fine with the last Ubuntu, so maybe it's Ibex thats the trouble.

Well, eternalnewbee, I have to thank you for trying to help, as your the only one that did.

---

### Post by wtfitsRICK on 2008-12-11
Okay, seriously.  Anyone?  I did the same thing, and it's seriously obnoxious not being able to remove it.
I've tried all the uninstall sites I've found, and they do nothing.
If I remove the applet from the dock, nothing has menus.  So I have to keep this.  And I don't want it.

Nobody knows?

---

### Post by sifix on 2008-12-13
I think that maybe work for you

gedit ~/.gnomerc

then comment the lines 

# Uncomment to load the GTK module

#export GTK_MODULES=globalmenu-gnome

# Uncomment to tell the GTK module to open a Gtk

# TreeView for all menus in the application you start.

#export GNOMENU_FUN=1

# Uncomment to disable global menu.

#export GNOMENU_DISABLED=1

# Uncomment to print a lot of debugging messages

#export GNOMENU_VERBOSE=1

# Uncomment to save the debugging messages to the given file.

#export GNOMENU_LOG_FILE=/tmp/gnomenu.log

# uncomment to disable the plugin for specific programs.

export GTK_MENUBAR_NO_MAC="fast-user-switch-applet"

---

### Post by etitor on 2009-02-19
> **kitsune ravo said:**
> Need help, now!

Here's the deal: I thought that making my Linux computer look like a Mac for a wile would be fun. So I did. And it was. That is, until I wanted to go back.

I Installed Global menu using the commands in the first post of this link: 
[http://ubuntuforums.org/showthread.php?t=241868&page=224](http://ubuntuforums.org/showthread.php?t=241868&page=224)

It worked until I wanted to get rid of it. I remove it from the panel, but my apps still don't have menus. I've looked in the package manager, it isn't listed. I've tried stuff like "sudo apt-get remove gnome2-globalmenu applet" and "sudo apt-get clean && sudo apt-get update && sudo apt-get install --reinstall -y libgtk2.0-0", and I've even gone so far as to remove my .gnomerc file and other gnome setting, but like a virus, this program will not give my menus back.

I need help really bad. Please, anybody who knows how to fix this without a reinstall, help me...

Try this alone: ```
sudo apt-get install libgtk2.0-0 --reinstall
```

I found this solution in [http://ubuntuforums.org/showthread.php?p=3121960&highlight=uninstall#post3121960](http://ubuntuforums.org/showthread.php?p=3121960&highlight=uninstall#post3121960) and it worked for me.

I should add: and don't forget to delete that file .gtkrc you created in your home folder.

---

### Post by nemomarlin on 2009-02-26
Kitsune,

This command worked for me,

Type in terminal: (Applications -> Accessories -> Terminal)

sudo apt-get remove gnome-globalmenu

also don't forget to uninstall the repositories. (System -> Administration ->Software Sources)

:)

---

### Post by cIIIz on 2009-08-14
it's easy:

open gconf-editor
```
gconf-editor
```

and then go to this path
```
/apps/gnome_settings_daemon/gtk_modules
```

There you see the entry for "globalmenu-gnome", just un-check it and it's back to normal. :KS

---

### Post by GeekGirl1 on 2009-09-21
That worked for me. Thanks!

---

### Post by Shpongle on 2009-11-28
> **cIIIz said:**
> it's easy:

open gconf-editor
```
gconf-editor
```

and then go to this path
```
/apps/gnome_settings_daemon/gtk_modules
```

There you see the entry for "globalmenu-gnome", just un-check it and it's back to normal. :KS

you are a hero!

---

### Post by MastroPino on 2010-02-05
Thanks mate, this must be on the wiki page of gnome-global-menu!!!

After that I follow ur tips, nautilus stop to stress me with this message:

```
Gtk-Message: Failed to load module "gnomenu-panel": libgnomenu-panel.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory

```

> **cIIIz said:**
> it's easy:

open gconf-editor
```
gconf-editor
```

and then go to this path
```
/apps/gnome_settings_daemon/gtk_modules
```

There you see the entry for "globalmenu-gnome", just un-check it and it's back to normal. :KS

---

### Post by aeqel on 2012-04-30
> **cIIIz said:**
> it's easy:

open gconf-editor
```
gconf-editor
```and then go to this path
```
/apps/gnome_settings_daemon/gtk_modules
```There you see the entry for "globalmenu-gnome", just un-check it and it's back to normal. :KS

Confirmed this working in Fedora 14 too. No problems at all.

---

