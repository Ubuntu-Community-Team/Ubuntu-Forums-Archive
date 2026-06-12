---
title: "cannot get 1680x1050 with Asus notebook..."
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2006-06-02
install went as expected,
booted as expected,
displays fine @ 1024x760

changing the display to 1680x1050 appears to "tile" a non widescreen image?  the mouse pointer is garbled and most of the tool bar graphics do not line up with the actual click actions.

could sombody please lend a hand with this?

Thanks.

1680x1050 WS w/ ati x700mobile pcie

---

### Post by hardyn on 2006-06-02
Fixed, 

see article " Screen Resolution on ATI mobility Radeon X700 "

very helpful...


one question, anybody know what the typical horizontal refresh for a 15.4" wxsga flat pannel should be?

dont have that info in my manual.

thanks.

---

### Post by kbuel on 2006-06-03
I have an Asus z71v 1680x1050 15.4" wxsga.  My xorg.conf is set to the following and it seems to work fine.

    HorizSync       28.0 - 84.0
    VertRefresh     43.0 - 60.0

---

