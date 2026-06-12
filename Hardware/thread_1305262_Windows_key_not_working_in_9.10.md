---
title: "Windows key not working in 9.10"
date: 2009-10-29
forum: Hardware
---

### Post by ezekiel000 on 2009-10-29
Does anyone know how to go about finding out why the windows key on my keyboard doesn't work? I've tried lots of combinations of keyboard type and layouts but no luck.

---

### Post by L33tN1nj4 on 2009-10-29
I do not believe the windows key is meant to work in Ubuntu because its a windows key and most likely the windows Dev's programmed the key to function with Windows, you might be able to find someone who has programmed the button to work in Ubuntu as well.

---

### Post by dummy910 on 2009-10-29
**System_>_Preferences_>_Keyboard**:
there you'll find all kinds of settings-key-mapping settings.

---

### Post by sliketymo on 2009-10-29
> **ezekiel000 said:**
> Does anyone know how to go about finding out why the windows key on my keyboard doesn't work? I've tried lots of combinations of keyboard type and layouts but no luck.

System>preferences>keyboard>>layout>layout options>ALT/win-key behavior.):P

---

### Post by Betialai on 2009-10-30
What do I have to do then to map that key (available in 99.9% of the keyboards and that was working just fine until this new release) to open the "panel's main menu" without needing to combine it with any other key?

---

### Post by Betialai on 2009-11-02
Anyone?

---

### Post by alexyz on 2009-11-06
This is driving me absolutely crazy, especially on my laptop.  I found this (haven't tried it yet).

[http://ramblings.narrabilis.com/wp/binding-windows-key-to-gnome-foothat-panel-menu/](http://ramblings.narrabilis.com/wp/binding-windows-key-to-gnome-foothat-panel-menu/)

but there's gotta be an easier way.  In all previous versions I've used for the last 3 years it was either (1) a simple selection in the keyboard options, or (2) you could set the keyboard shortcut.  (I don't remember details.)

Now if you try to set a keyboard shortcut, when you press the "start" key, nothing happens.

---

### Post by Drood on 2009-11-06
Just go to to the keyboard shortcuts and look for super, thats what it is called I believe.

---

### Post by alexyz on 2009-11-06
Thanks Drood, that may have been true in earlier versions but not now.  Here are the details as I see it:

System > Preferences > Keyboard Shortcuts > Desktop > Show the panel's main menu

* press win key, nothing happens.  I believe this is because the win key is treated as a modifier and only recognized in combination with other keys.

System > Preferences > Keyboard > Layouts > Layout Options > Alt/Win behavior

* I've tried every setting here and it makes no difference

Unless I've gone crazy there was another way to do it in the past.  I've been running Ubuntu over 3 years on many different machines and this has always been one of the first settings I would change.

---

### Post by alexyz on 2009-11-06
short answer - run this from a command line:
```

gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L"
```

explanation here:

[http://www.webupd8.org/2009/10/ubuntu-karmic-make-super-key-bring-down.html](http://www.webupd8.org/2009/10/ubuntu-karmic-make-super-key-bring-down.html)

sheesh, that was harder to figure out than it should have been!  But I'm happy now ):P

search engine keywords:  win windows super super_l start menu key keyboard shortcut binding applications main

---

### Post by ezekiel000 on 2009-11-06
Thanks alexyz I had given up on getting it working. I don't really use the win key but it's annoying to have anything on my pc that doesn't work.

---

### Post by alexyz on 2009-11-06
Hey ezekiel000 if you see this you might mark this thread as SOLVED (in thread tools menu).

---

### Post by dow mathis on 2009-11-22
> **alexyz said:**
> short answer - run this from a command line:
```

gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L"
```

explanation here:

[http://www.webupd8.org/2009/10/ubuntu-karmic-make-super-key-bring-down.html](http://www.webupd8.org/2009/10/ubuntu-karmic-make-super-key-bring-down.html)

sheesh, that was harder to figure out than it should have been!  But I'm happy now ):P

search engine keywords:  win windows super super_l start menu key keyboard shortcut binding applications main

ABSOTUTELY FANTABULOUS!!!  I've been looking for that forever.  Thanks!

---

### Post by ertayone on 2010-01-16
> **alexyz said:**
> short answer - run this from a command line:
```

gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L"
```explanation here:

[http://www.webupd8.org/2009/10/ubuntu-karmic-make-super-key-bring-down.html](http://www.webupd8.org/2009/10/ubuntu-karmic-make-super-key-bring-down.html)

sheesh, that was harder to figure out than it should have been!  But I'm happy now ):P

search engine keywords:  win windows super super_l start menu key keyboard shortcut binding applications main
I'm running an HP Pavilion laptop and this worked for me. Thanks very much! Hopefully in later releases we won't have to access this feature by command line.

---

### Post by anantshri on 2010-03-19
Few Concerns,

in all the links i found this command will mark windows Left key solely for opening the menu.

What i am looking for is a way to accomplish following task.

[LIST=1]
[*]I want windows key on left or right to toggle menu. as well as esc to be able to close menu.
[*]I want <win>+e , Win+T, win+d shortcodes to work.
[/LIST]

Can the above be accomplished. if yes then how.
and if no then why not.

---

