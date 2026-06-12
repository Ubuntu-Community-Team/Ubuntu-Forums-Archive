---
title: "Remapping the 'function' key"
date: 2008-08-08
forum: Hardware
---

### Post by rufus25 on 2008-08-08
Hi all. I just bought a 'Happy Hacking Keyboard' to get rid of the numpad and some other keys I don't use, etc., mostly to get a not so broad keyboard. The keyboard got a function key to activate keys like 'Home' and such, like some laptop keyboards do.

Now I would like to put the left function key to another place, preferably swap it with the control key. The problem is, I can't get the keycode for the function key, xev acts as if nothing is pressed.

Does the function key only work "on the keyboard level", so no keypress event is send until a valid combination is pressed? Or is there a way to remap the function key?

---

### Post by sergiom99 on 2008-08-08
I set my left win key as a "compose key" for my spanish characters by adding this to the xorg.conf file.
```
 Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
# agregado para tratar de usar LWIN como Compose Key -- 08/06/08
        Option         "XkbOptions" "compose:lwin"
EndSection
```

Maybe you can explore along this line.
Good luck!

---

### Post by Gaygerbil on 2010-08-12
Bumping this 2 years later cuz I'm curious now.

I usually use the keyboard shortcuts Alt +1 (2, 3, 4, 5 etc.) to launch different applications.

Now I'm thinking of using Fn + Z (X, C, V, B etc.) to launch these applications instead. It just saves my hand and lets me put the Alt keys to other uses. 

I can't use the Fn key for anything other than what it was mapped to do however, any ideas on how to get around this?

---

### Post by SoFl W on 2011-07-12
I am going to bump this because I can't get the left compose key to work under xfce either.  
I have no right compose (windows) key so the instructions [here]("https://help.ubuntu.com/community/ComposeKey") did not work.  (I tried)  I also tried replacing "rwin" with "lwin"

---

