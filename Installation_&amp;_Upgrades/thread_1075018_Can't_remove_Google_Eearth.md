---
title: "Can't remove Google Eearth"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by ahsun on 2009-02-19
Hi,

I installed Google Earth, was giving me problems, so i removed it Using rm..
the only thing is that i have the window looking shell with Google earth next to it in Applications>Internet.. I don't know how to delete that.  Everytime I clik on it, I get the .googleearth folder in my home dir. 
Sorry new to ubuntu, just trying different things,, figure this would be the best way to learn..

Any help will be appreciated.

---

### Post by taurus on 2009-02-19
If you want to remove ~/.googleearth, you can do so from a terminal with

Applications -> Accessories -> Terminal
```
rm -rf ~/.googleearth
```
And if you want to remove it from Applications -> Internet, look in the System -> Preferences -> Main Menu.

---

### Post by ahsun on 2009-02-19
I tried the above command.. didn't work.. well the command worked but the window looking icon its not Google Earth Icon, but just a blank window and googleearth is still in application>internet.
Tried System>pref>Main Menu.. Nothing happens..

---

### Post by taurus on 2009-02-19
Did you remove the Google Earth icon from System -> Preferences -> Main Menu -> Internet?

---

### Post by ahsun on 2009-02-19
Well, when I go to system>Pref>main menu
nothing happens.. I click on it nothing popus up.

---

### Post by ahsun on 2009-02-19
got it.. I launched alacarte from Terminal and then got the page... thanks

---

### Post by beameup on 2009-04-20
FYI: In Google Earth 5, just go in the Google-earth folder that's located in your Home folder and there is an uninstaller

---

