---
title: "Screen Rotate ASUS 1001P"
date: 2011-03-17
forum: Hardware
---

### Post by paradoxdream on 2011-03-17
hello,
   I was wondering if some one could help me rotate my net-book screen so I can use it like a reader. In windows I just push crtl+alt+arrow and it will rotate my screen any direction but in Ubuntu it switches desktops if some one could help me out with this would be much appreciated.

Neetbook - ASUS 1001P
Ubuntu - Netbook 10.10

---

### Post by azzamite on 2011-03-17
I have used xrandr to rotate the screen:
```
me$ xrandr -o left
```
To return to normal use:
```
me$ xrandr -o normal
```

Check the manual page for details, this command does plenty of interesting stuff.

---

### Post by paradoxdream on 2011-03-17
> **azzamite said:**
> I have used xrandr to rotate the screen:
```
me$ xrandr -o left
```To return to normal use:
```
me$ xrandr -o normal
```Check the manual page for details, this command does plenty of interesting stuff.

Wow that worked like a charm thx man now I can read my ebooks and with the F11 button can read my manga also. Now for me Ubuntu Notebook has official surpassed the starter windows. If you had not of shown me this was possible and on the easy side I would of just wiped Linux off the second partition.:P:P:P

---

### Post by bluereg133 on 2011-03-18
Thanks for a new solution about "Screen Rotate ASUS 1001P". I will try further.

---

### Post by hane on 2011-04-06
Thanks to know about 'xrandr to rotate the screen'. It really works nice.:D





Alex

---

