---
title: "Map keyboard keys to mouse buttons?"
date: 2008-11-13
forum: Hardware
---

### Post by gcbzzzz on 2008-11-13
since the [old, unsolved, thread]("http://ubuntuforums.org/showthread.php?t=500116") i found initially is closed, i'm openning this one to post the solution. I had to find this because asus decided that it's ok to sell a notebook with only two mouse buttons in 2008. lame.

before, some more keywords:
xmodmap. Keysym to mouse button.

**Required packages:**
```
apt-get install xbindkeys xautomation

```
xautomation will provide xte. which simulates buttons and keypresses.
xbindkeys maps a key/mouse combination to commands.

now, tie everything together:
```
echo (xbindkey '(Menu) "xte 'mouseclick 2'") > ~/.xbindkeysrc.scm

```
this will make pressing the Menu key, simulate a middle mouse click.

*edit* forgot to mention, you must  now have xbindkeys running :)
for now i'm simply opening a terminal and typing _xbindkeys &_ and closing it... will add to xsession later. but i doubt i came back here to document. you're on your own :)

original idea from: [http://www.gentoo-wiki.info/Saitek_Slimline_Multimedia_Keyboard#Binding_.22Keyboard_Mouse_Buttons.22_to_keysyms](http://www.gentoo-wiki.info/Saitek_Slimline_Multimedia_Keyboard#Binding_.22Keyboard_Mouse_Buttons.22_to_keysyms)

---

### Post by jpkotta on 2008-11-13
Also, you can do Shift-NumLock, and the number pad moves the pointer.  NP_5 is mouse button 1.

---

