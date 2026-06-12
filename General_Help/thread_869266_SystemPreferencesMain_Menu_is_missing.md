---
title: "System/Preferences/Main Menu is missing"
date: 2008-07-24
forum: General Help
---

### Post by Ozdemon on 2008-07-24
Somehow I have managed to delete the Main Menu from the System/Preferences menu.  I have tried to re-install by removing and re-installing gnome-main-menu and libslab, but that didn't work.

Can anyone help as to how I get the Main Menu back?  :confused:

---

### Post by Het Irv on 2008-07-24
in the terminal type:
```
alacarte
```
that will open the Menu Editor for you to put it back into the menu.

---

### Post by coffeecat on 2008-07-24
> **Ozdemon said:**
> Somehow I have managed to delete the Main Menu from the System/Preferences menu. 

Whoops! I can see how that would be a problem trying to open Main Menu to get Main menu back in the menu. :?

Open a terminal, and:

```
alacarte
```

Then you should be able to go to Preferences and re-tick Main Menu. If that's disappeared for any reason, this is what you need to create a new item:

Type: Application

Name: Main Menu

Command: alacarte

---

### Post by kidux on 2008-07-24
I assume you mean you deleted it from the gnome-panel? If so it should be a simple matter of right-clicking it and adding a launcher, which it should be one of the default ones in there.

Edit: Whoops looks like I was beaten to the punch! LOL!

---

### Post by Ozdemon on 2008-07-25
Ah, when I typed in alacarte I got a msg saying alacarte was not installed but if I wanted it I needed to enter sudo apt-get ...etc

So I did that and problem solved!

Many thanks.

---

