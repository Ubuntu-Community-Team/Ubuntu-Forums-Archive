---
title: "Numeric keypad row inverted"
date: 2014-02-11
forum: Hardware
---

### Post by pico977 on 2014-02-11
Hi

I have a problem with my keypad
Ubuntu recognizes the first row (keys 7, 8 and 9) as if it were the last (keys 1, 2 and 3) and vice versa.
So if I write 123456789, I obtain 789456123.

I try to use

```
xmodmap .xmodmaprc
```

where this is .xmodmaprc file:
```
keycode  87 = KP_Home KP_1 KP_Home KP_1 a NoSymbol a
keycode  88 = KP_Up KP_2 KP_Up KP_2 b NoSymbol b
keycode  89 = KP_Prior KP_3 KP_Prior KP_3 c NoSymbol c
keycode  79 = KP_End KP_7 KP_End KP_7 equal NoSymbol equal
keycode  80 = KP_Down KP_8 KP_Down KP_8 x NoSymbol x
keycode  81 = KP_Next KP_9 KP_Next KP_9 colon NoSymbol colon

```

But the solution works fine just some minutes, then I return to the initial situation.

I tryed to reconfigure the keyboard with
```
sudo dpkg-reconfigure keyboard-configuration
```

Again I obtain a temporany solution.

Could you help me, please?

Thanks and sorry for my english

---

### Post by benjismith on 2014-02-11
check out this post, hope it helps :)
[http://askubuntu.com/questions/371530/ubuntu-13-10-numeric-pad-type-wrong-numbers](http://askubuntu.com/questions/371530/ubuntu-13-10-numeric-pad-type-wrong-numbers)

---

### Post by pico977 on 2014-02-12
Good

Many thanks
bye

---

