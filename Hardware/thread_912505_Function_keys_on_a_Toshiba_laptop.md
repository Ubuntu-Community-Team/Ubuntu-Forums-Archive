---
title: "Function keys on a Toshiba laptop"
date: 2008-09-06
forum: Hardware
---

### Post by ice2921 on 2008-09-06
Anyone know how to get the funcion keys to work on a Toshiba Satellite M45-S265 laptop?

---

### Post by sergiom99 on 2008-09-07
you can try installing kmilo and/or keytouch.
keytouch lets you define your own keyboard settings.
Good luck.

---

### Post by NickLanam on 2008-09-07
I probably only say this 'cause I've been messing with it so much lately, but I'd just use xev and xmodmap to manually define them.
```

xev
!(press your fn key with mouse over the white window that pops up
!note the number after "keycode" in the keyRelease event
!(kill that window once you've noted that number)
xmodmap -e keycode <thatcode>=Function
!I don't remember if it's -e, and don't remember which string binds it to Function key

```

---

### Post by ice2921 on 2008-09-08
I have no idea how do do that. Can anyone walk me through it/

---

