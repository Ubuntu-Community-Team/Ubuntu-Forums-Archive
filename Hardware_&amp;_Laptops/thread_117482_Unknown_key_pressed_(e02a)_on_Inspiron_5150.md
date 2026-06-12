---
title: "Unknown key pressed (e02a) on Inspiron 5150"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by mabster on 2006-01-15
Hi, I've got this in my logs:

```
[4300877.195000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300877.195000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
```

Now the problem here is that I don't know what the unknown key is (ie. I'm not sure what to press to get it to trigger).  Is there a way I can find out?  This is really cluttering up my logs ;)

---

### Post by Mr_Grieves on 2006-01-15
Have you tried the recommendation?

> 
Use 'setkeycodes e02a <keycode>' to make it known.


Keycode is as I can understand from you're error message: 0xaa

But you should perhaps check that on google first before doing anything.. so that you don't "destroy" some important key or you're keyboard handling.. eheh.

---

### Post by dcstar on 2006-01-19
[QUOTE=mabster]Hi, I've got this in my logs:

```
[4300877.195000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300877.195000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
```

Now the problem here is that I don't know what the unknown key is (ie. I'm not sure what to press to get it to trigger).  Is there a way I can find out?  This is really cluttering up my logs ;)[/QUOTE]
[http://ubuntuforums.org/showthread.php?p=669419&posted=1#post669419](http://ubuntuforums.org/showthread.php?p=669419&posted=1#post669419)

---

