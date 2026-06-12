---
title: "What will happen if removing ubuntu-desktop?"
date: 2008-08-21
forum: General Help
---

### Post by Pidgin on 2008-08-21
I wish to try Ubuntu Studio on my Ubuntu installation. But if I install the package ubuntustudio-desktop, it is said that the package ubuntu-desktop will be removed. Why should the most important package ubuntu-desktop be removed? What will actually happen if the package is removed? Will my Ubuntu still exist? And my settings, documents, installed applications and games?
Thanks!

---

### Post by Titan8990 on 2008-08-21
It will remove the gnome desktop. Everything will be the same except there will be no graphical interface. Your Gnome settings will be lost. After the desktop is removed you will be presented with a CLI only system. Once you are in the CLI system you can do this to reinstall the desktop:

sudo apt-get install ubuntu-desktop

Usually takes about a 30min to reinstall the desktop.

---

### Post by Pidgin on 2008-08-21
> **Titan8990 said:**
> It will remove the gnome desktop. Everything will be the same except there will be no graphical interface. Your Gnome settings will be lost. After the desktop is removed you will be presented with a CLI only system. Once you are in the CLI system you can do this to reinstall the desktop:

sudo apt-get install ubuntu-desktop

Usually takes about a 30min to reinstall the desktop.

But if I replace ubuntu-desktop with ubuntustudio-desktop?

---

### Post by Too Late on 2008-08-21
As far as I know, ubuntu-desktop is a so called meta package, so uninstalling it won't uninstall anything else, but installing it will install many other packages which are depended. But I'm not sure and I wonder why it should be uninstalled when installing ubuntustudio-desktop. Also, I don't know what's the difference between removal and complete removal.

---

### Post by Titan8990 on 2008-08-21
Your statement is incomplete?

---

### Post by Too Late on 2008-08-21
> **Titan8990 said:**
> Your statement is incomplete?
Mine? :confused:

---

### Post by Titan8990 on 2008-08-21
No this statement:

> But if I replace ubuntu-desktop with ubuntustudio-desktop?

It begins with "but if" and only has one argument. 


EG - but if I do argument1 then argument2.

---

### Post by jerome1232 on 2008-08-21
> **Too Late said:**
> As far as I know, ubuntu-desktop is a so called meta package, so uninstalling it won't uninstall anything else, but installing it will install many other packages which are depended. But I'm not sure and I wonder why it should be uninstalled when installing ubuntustudio-desktop. Also, I don't know what's the difference between removal and complete removal.

Removing it will do a whole lot of nothing as Too Late was saying it's just a "meta package" that brings in all the packages for a gnome desktop.

Complete removal purges configuration files where as just removal leaves the configuration files.

---

### Post by Pidgin on 2008-08-21
> **Titan8990 said:**
> No this statement:



It begins with "but if" and only has one argument. 


EG - but if I do argument1 then argument2.

Oh, sorry. The complete statement should be: But if I replace ubuntu-desktop with ubuntustudio-desktop, what will happen? I thought the main clause could be omitted.

---

### Post by Titan8990 on 2008-08-21
I would try it and see. Worst that could happen is you will have to reinstall the desktop. From the looks of other user replies you won't even have to do that.

---

### Post by jerome1232 on 2008-08-21
Ubuntu Studio is really Ubuntu with a different theme (a very nice theme btw) and some extra multimedia editing software.

All it's going to do is re-theme your desktop and add some extra software.

---

### Post by 3rdalbum on 2008-08-21
Removing ubuntu-desktop is completely harmless - it doesn't remove any other packages at all. You don't lose your GUI, nothing like that at all, so there's nothing to be scared of.

---

### Post by Pidgin on 2008-08-21
I tried it, entering the command below:
```

sudo apt-get update
sudo apt-get install ubuntustudio-desktop

```
Then it installed many other packages and removed ubuntu-desktop and ubuntu-sounds. After restarting, I had the really cool Ubuntu Studio interface. But some games could not sound!!!
Games which cannot sound:
[LIST]
[*]SuperTux 2
[*]Supertuxkart
[*]Wormux
[*]Alien Arena
[/LIST]
Games which can sound:
[LIST]
[*]Chromium
[*]Warzone 2100
[*]OpenArena
[/LIST]
Music and media player software seems normal. That's really strange! What should I do to make these games normal?
[COLOR="Red"]**[SIZE="7"]Help!!![/SIZE]**[/COLOR]
:confused::confused::confused:

---

### Post by mb_webguy on 2008-08-21
> **Titan8990 said:**
> Your statement is incomplete?

And your statement is apparently a question.  :wink:

---

