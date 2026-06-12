---
title: "virtual resolution max 2048?"
date: 2009-06-03
forum: Hardware
---

### Post by scales on 2009-06-03
hi all, i know that my intel 945 vid card in my eee1000he is limited (with compiz) to a virtual resolution of 2048x2048.  so here is my thought,

my laptop display is 1024x600
my external monitor is 1440x900

I can have them above and below each other, but i would like them side by side, which will use a virtual resolution of 2464x900, which is too big.

My question is, is there any way to make the virtual resolution be 2048x900 and just have the screens overlap? is that even possible?

---

### Post by scales on 2009-06-03
eureka! you can! awesome!
>    1.
      xrandr --output VGA --auto --pos 0x0 --output LVSD --auto --pos 0x0


just make the 0x0 the correct coordinates

---

