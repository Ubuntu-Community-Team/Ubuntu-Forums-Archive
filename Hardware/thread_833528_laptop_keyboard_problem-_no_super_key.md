---
title: "laptop keyboard problem- no super key"
date: 2008-06-18
forum: Hardware
---

### Post by ddixonr on 2008-06-18
I've had this problem for a long time now, and I thought I give it another shot. When I first installed Gutsy about a year ago, everything worked fine. After a few updates, I noticed the Super key not working. Then the "right-click key". Actually the right-click key initiates the screen saver & locks the screen.

I've tried to use different layouts, but none make any improvements. I have a Toshiba Satellite A105 S4284 and currently running Hardy. In case it helps, here is the keyboard section of Xorg.conf:

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Any help is appreciated. Thanks

---

