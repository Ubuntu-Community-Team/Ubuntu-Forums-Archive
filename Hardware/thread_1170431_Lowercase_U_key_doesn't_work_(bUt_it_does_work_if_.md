---
title: "Lowercase U key doesn't work (bUt it does work if I press the shift bUtton)"
date: 2009-05-26
forum: Hardware
---

### Post by hozzy on 2009-05-26
I have done some searching aroUnd and I can't find anything helpfUl. My lowercase U doesn't work. If I press shift and U it works, or if i have capslock enabled, [start capslock]HOLD SHIFT AND u I GET A LOWERCASE u [END CAPSLOCK]. All other keys work normally.

Has anyone heard of this?

Is there a way to know what the keyboard is sending when I press U? In terminal, when i press U, nothing comes Up, bUt the blinking cUrsor changes, so I know some information is being sent, jUst wondering what information is being sent.

Also Fn U works (works as a left arrow)

With nUm lock on, press the U key resUlts in a 4 (which is correct according to my keyboard)

At the end of the day, the key works, Uppercase U works, Ctrl U work (Underline), shift U works, capslock shift U works, Fn U works, NUmlock U works, they key jUst doesn't work Unless there is some modifer command.

When capslock is on, the U key only works with conjUnction with the shift/fn/ctrl bUtton.

I have an asUs eee 1000h, rUnning UbUntU 8.10, I am cUrrently traveling and don't have a dvd rom drive nor do I want to try a new distro (I'm traveling and I don't want to enjoy myself). I won't be switching oUt for a new keyboard so please don't tell me to do that. LinUx is the only working os on this machine.

Thanks in advance

---

### Post by hozzy on 2009-05-27
Anyone?? It is frUsterating bUt there mUst be a way to fix it.

---

### Post by plewisfdx on 2009-05-27
Change the keyboard settings.  (I use xubuntu and its located at Applications->Settings->Keyboard->Layout )

What is your current selection there, and what else have you tried?

Have you tried reconfiguring the keyboard?

```
sudo dpkg-reconfigure -plow console-setup
```

I think there's a way to see the output of a keypress, but I can't locate it right now after a few mins of googling.

---

### Post by Mazin on 2009-05-27
The console program xev will show you what input events occur.

---

