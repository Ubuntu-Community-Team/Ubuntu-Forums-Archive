---
title: "How change the layout keyboard"
date: 2012-08-15
forum: Hardware
---

### Post by kennyruffles on 2012-08-15
I have two pcs. In one of them the keyboard is right and the other don't.
In the correct one, i put enter the command:

> setxkbmap -print
xkb_keymap {
    xkb_keycodes  { include "evdev+aliases(qwerty)"    };
    xkb_types     { include "complete"    };
    xkb_compat    { include "complete"    };
    xkb_symbols   { include "pc+br+inet(evdev)"    };
    xkb_geometry  { include "pc(pc105)"    };
};


I wanna copy this kbmap to the other one. How can i do that?

---

### Post by irv on 2012-08-15
I don't know what version of Ubuntu you are using?

[http://www.wikihow.com/Change-Keyboard-Layout-in-Ubuntu]("http://www.wikihow.com/Change-Keyboard-Layout-in-Ubuntu")

[http://superuser.com/questions/421227/how-do-i-configure-keyboard-layouts-in-ubuntu-12-04]("http://superuser.com/questions/421227/how-do-i-configure-keyboard-layouts-in-ubuntu-12-04")

Here is a couple of links to try.

---

### Post by kennyruffles on 2012-08-15
I'm using version 11.10, i tried to change with the UI, but it didn't work. 
I don't wanna change the xorg. Is there other way?

---

### Post by irv on 2012-08-16
To be honest with you I don't know how to do this, but you could write a script file to change the keyboard and then run it at startup. I'm not into writing scripts so maybe someone else can jump in here and tell you how to do this.

EDIT: If this is a fairly new install you could just do a fresh install and set the keyboard on the install.

---

### Post by kennyruffles on 2012-08-16
Do you have some example of the command to change the keyboard layout to this one?
Unfortunately i can't make a fresh install on this computer.

---

### Post by irv on 2012-08-16
I am using Ubuntu 12.04 and it should be the same in 11.10. Go to system setting and select keyboard layout. you can change option by selecting the option button. Also click on the little keyboard icon on the bottom and it will open a layout of your keyboard. Maybe you can make the changes here.
[ATTACH]222776[/ATTACH]  [ATTACH]222777[/ATTACH]  [ATTACH]222778[/ATTACH]  [ATTACH]222779[/ATTACH]

---

### Post by Nwe Nwe on 2012-12-21
> **irv said:**
> I am using Ubuntu 12.04 and it should be the same in 11.10. Go to system setting and select keyboard layout. you can change option by selecting the option button. Also click on the little keyboard icon on the bottom and it will open a layout of your keyboard. Maybe you can make the changes here.
[ATTACH]222776[/ATTACH]  [ATTACH]222777[/ATTACH]  [ATTACH]222778[/ATTACH]  [ATTACH]222779[/ATTACH]


I do the way you say..but in 3th figure, the keyboard icon is not inactive. I can't do anymore. I use Ubuntu 12.10. I can see the font I want, but i can't type it. My wanted e.g. font.ttf is under ~/.local/share/font/ . But, I can't type the font. Please share more. Thanks in advance.

---

### Post by irv on 2012-12-21
> **Nwe Nwe said:**
> I do the way you say..but in 3th figure, the keyboard icon is not inactive. I can't do anymore. I use Ubuntu 12.10. I can see the font I want, but i can't type it. My wanted e.g. font.ttf is under ~/.local/share/font/ . But, I can't type the font. Please share more. Thanks in advance.

I am using 12.10 now also, and if you select options on the screen before the last one you can change any option you want.

---

