---
title: "Logitech G15  xbindkeys and xvkbd issue"
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by mback99 on 2007-12-20
I try to remap certain keys on my new G15 keyboard

Just as a test I try to  map F1 to one of the speciall G keys on my
keybord

This is my entry in .xbindkeysrc

"/home/mix/.g15macro/g15.sh  &"
 m:0x10 + c:137
 Mod2 + NoSymbol

and this is my macro g15.sh

#!/bin/bash
sleep 0.1
xvkbd -text \XK_F1

and then I run  killall -HUP xbindkeys
but it doesn't work.. Any help would be appreciated  :)
....

---

