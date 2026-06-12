---
title: "Java prevents xbindkeys from recieving button presses"
date: 2012-05-05
forum: Hardware
---

### Post by Superyoshi on 2012-05-05
I bought a Logitech G400 today. It works fine just after plugging in, but since it had two thumb buttons I thought about using it. I tried to do a kind of "Panic Button" in Minecraft by simulating a press on 2 (second slot, where usually my sword is) when hitting the Thumb2 button.

After some searching and trying out, I ended up with this in xorg.conf:
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "evdev"
    Option        "CorePointer"
    Option        "Name"    "Logitech Gaming Mouse G400"
EndSection
```And this in .xbindkeysrc:
```
# MC Panic Button
"xte 'key 2'"
  b:9
```And it does work - if I press Thumb2 in a text field, a 2 appears. But trying it in Minecraft it fails. If the chat is open and the mouse is not trapped a 2 appears in the chat, and it successfully switches to the right slot if you are in-game, but without clicking into the window. As soon the mouse is trapped, xbindkeys stops showing button presses (I check via xbindkeys -v -n).

Is there any workaround for this problem, or some other way to do what I am trying to do?
(also, while it's not really neccesarry: if anyone knows how to make this bind work just in Minecraft, a how-to would be greatly appreciated!)

---

