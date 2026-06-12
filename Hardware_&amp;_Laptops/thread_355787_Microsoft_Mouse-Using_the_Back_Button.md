---
title: "Microsoft Mouse-Using the Back Button"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by Dylnuge on 2007-02-07
I am having a problem with my Microsoft IntelliMouse Wireless Explorer 2. It has two buttons on the side of it that act as back and forward buttons. I was wondering if it was possible to get them to work in Firefox (display last page), instead of acting as a left mouse button. Thanks.

---

### Post by kebes on 2007-02-07
I don't know if this is the best way...

You can use the program "xev" to display the "keycode" for any keyboard or mouse event. Try it, you'll see different numbers appear in it whenever you press a key or whatever.

Then you can use "xmodmap" to create an association between a keycode and a keystroke (so you can set a certain key or mouse button to be "enter" or "backspace" or whatever). You can put the xmodmap commands in a script that runs whenever you login, of course.


I've never done this with mouse keys, but I believe xmodmap can still be used. Hopefully a bit of searching on those topics will yield a solution...

Good luck.

---

### Post by johnc4510 on 2007-02-07
I used this guide for my Logitech LX7, it should work for you too.
[https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons](https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons)

Follow Dapper config about middle of page for xorg.conf

good luck

---

