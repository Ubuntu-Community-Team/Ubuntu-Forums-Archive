---
title: "Keyboard has no insert key"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by rai4shu2 on 2007-02-13
I have a strange situation here. Perfectly normal US Logitech keyboard that nevertheless has no "Insert" key. It's not normally a problem, but every now and then you'll run into a situation where something needs it like a text editor.

Anyway, here's the solution I came up with (I use the PrtScr key for Insert, as I already reconfigured screenshot to be Win+S anyway).

```
xmodmap -e "keysym Print = Insert"
echo -e "keysym Print = Insert" > ~/.Xmodmap
```

Is there some other (more elegant) way to do this or something about these Logitech keyboards I should know about as far as the missing Insert key goes?

---

### Post by socceroos on 2008-02-20
Thanks for this! Much appreciated!

I was searching around for this exact solution for over an hour.

---

