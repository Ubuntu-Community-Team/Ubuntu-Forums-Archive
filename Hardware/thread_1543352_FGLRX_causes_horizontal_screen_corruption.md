---
title: "FGLRX causes horizontal screen corruption"
date: 2010-07-31
forum: Hardware
---

### Post by cob on 2010-07-31
I just installed 10.04 32-bit, and I have an ATI HD 4200 on-board video IGP.  I installed the hardware driver using the GUI method, and the desktop looks like this now.  This input form is heavily corrupted, so I'll review this post in a moment and make sure it's not badly mistyped.  :) 

Screenshot...if I try to use any menus, they end up looking like the window title bar in this screenshot.

[http://imgur.com/lSYwr.png](http://imgur.com/lSYwr.png)

---

### Post by Ivan.Calderon on 2010-11-17
Sorry to revive this thread, but this affects me aswell, its slightly noticeable on the mouse cursor with compiz activated. On metacity almost 60% of the screen is corrupted.

Open source driver works just fine. Also works fine with MS OSes.

mainboard is an ECS a785gm-m7
Ubuntu 10.10 32 bits with pae kernel (because of ram > 3gb)
installed fglrx from "Additional drivers"

EDIT: 'Fixed' by switching from the -generic-pae kernel to the -generic one.

---

