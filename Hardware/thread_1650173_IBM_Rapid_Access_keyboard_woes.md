---
title: "IBM Rapid Access keyboard woes"
date: 2010-12-21
forum: Hardware
---

### Post by AprilHare on 2010-12-21
I have a IBM Rapid Access PS/2 keyboard (model KB-9930 37L2631; I believe this is what is otherwise called Rapid Access II but I may be mistaken).
Ubuntu 10.10 makes a mess of the multimedia keys for this keyboard; no matter what keyboard is selected in preferences they don't work right. I have read at least one other Ubuntu user has had problems with this keyboard type in the past however the matter wasn't resolved.
Fortuately (?) this problem is shared with Windows 7 due to lack of drivers for Vista/7 so I had cause to muck around and find the PS/2 keycodes associated with the multimedia keys using KeyTweak under Windows 7. Remapped, they work great under Windows; the little LED under the Standby button doesn't seem to do anything but beyond that I can get full functionality.
My question is: how do I remap these keys to work under Ubuntu? Would I be better off asking for proper support, and if so where do I ask?

For reference:
Multimedia function keys:
Green E025 (hex)
Dark blue E026
Yellow E032
Purple E017
Orange E030
Light blue E02E
White (standby) (E05F)

Multimedia audio keys:
Stop E020
Play/pause (E022)
Volume down E021
Volume up E023
Last Track E024
Next Track E012
Mute E01E

All other keys are standard except for document back/forward keys both sides of the up arrow key - both for some reason both reported back as 38 hex; don't ask me why - they worked perfectly and distinctly under Windows 7 otherwise.

---

