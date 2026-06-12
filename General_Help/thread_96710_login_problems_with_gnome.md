---
title: "login problems with gnome"
date: 2005-11-29
forum: General Help
---

### Post by agusnit on 2005-11-29
Hi
i've just started to use ubuntu on my vaio pcg-z1xfp with dual boot and in the moment i get to the login window, my keyboard doesnt work, i can only write spaces and delete them but i cant use letters!!!
if i ener ctrl-alt-f1 and then try to write anything my keyboard works just fine.
How can i enter gnome like this?

---

### Post by Remmelas on 2005-11-29
It sounds like you've got problems with the keyboard layout chosen for your xorg.conf file.  Can you post the keyboard section from your xorg.conf file?  For example, mine uses xorg rules, a pc105 model identifier, and a 'U.S.' layout.


```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

```

---

