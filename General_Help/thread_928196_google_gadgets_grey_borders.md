---
title: "google gadgets grey borders"
date: 2008-09-23
forum: General Help
---

### Post by benjaminjames on 2008-09-23
[[img=http://img131.imageshack.us/img131/4453/screenshotrl9.th.png]](http://img131.imageshack.us/my.php?image=screenshotrl9.png)[[img=http://img131.imageshack.us/images/thpix.gif]](http://g.imageshack.us/thpix.php)
 the three gadgets in the centre of the screen are google gadgets and i dont know how to get rid of the grey borders, can anyone help?? oh btw the trash can is a screenlet

---

### Post by hoa3r on 2008-09-23
You have to turn compiz desktop-effects on or use this command to turn compositing manager on:

```
gconftool-2 -s --type bool /apps/metacity/general/compositing_manager true
```

After that you should have transparent for your google gadgets.

---

### Post by benjaminjames on 2008-09-23
well i have a dual monitor setup and for some reason it is not possible to turn compiz on when using this setup (big bug that hasnt been resolved as far as i know), i trid tyrping the command you wrote out into the terminal but nothing happened either in the terminal or on the desktop? what next any clues thank.

---

### Post by hoa3r on 2008-09-23
What graphic card do you have? I have compiz with dual monitor and bigdesktop with the latest ati driver.

If compiz don't work, gnome compositing manager should work.

Did you see any shadows under your windows? Try restart your desktop.

---

### Post by benjaminjames on 2008-09-25
ok so no shadows under my windows and ive tried restarting my desktop no luck, ive got an nvidia 7300le. so is there any commands i can type into the termionla to get the transparency on?? without compiz

---

### Post by hoa3r on 2008-09-25
This code in the console should enable compositing manager:

```
gconftool-2 -s --type bool /apps/metacity/general/compositing_manager true
```

So i wonder why it's not working for you.
Another way is to start gconf-editor (in console or launcher) and go to /apps/metacity/general and enable compositing_manager there.

An easy way to do that and other cool things just install ubuntu-tweak: [http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)

---

### Post by benjaminjames on 2008-10-02
/tmp/ubuntu-tweak_0.3.5-1~ppa1_all-1.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.
got this error message when i tried to open ubuntu tweak any ideas? tnx

---

