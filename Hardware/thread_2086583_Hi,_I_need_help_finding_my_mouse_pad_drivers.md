---
title: "Hi, I need help finding my mouse pad drivers"
date: 2012-11-21
forum: Hardware
---

### Post by andreamillspaugh on 2012-11-21
Hi, everyone I have a Presario CQ56 112nr, and Ubuntu works with out any problems, In windows I would turn off my mouse pad because it will get in the way when I type, is there any drivers for Ubuntu that will let me turn off the mouse pad because I us a mouse instead because i can stand the mouse pad, so I us a out side mouse, thanks :)

---

### Post by sysone on 2012-11-21
try this :

System Settings -->Mouse n Touchpad   and try to make your adjustments.

Let us know

---

### Post by dannyboy79 on 2012-11-21
you may be able to disable it within your BIOS
OR
you could try one of the function keys (Lenovo Thinkpad T500 it's Fn+F8)
OR
you can try
```
synclient TouchPadOff=1
```
you may have to do that every reboot though.

Good luck

---

### Post by andreamillspaugh on 2012-11-21
Thanks everyone I used this and it worked

```
synclient TouchPadOff=1
```

---

