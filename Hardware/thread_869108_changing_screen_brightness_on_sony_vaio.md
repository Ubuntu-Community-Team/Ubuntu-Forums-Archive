---
title: "changing screen brightness on sony vaio"
date: 2008-07-24
forum: Hardware
---

### Post by T2manner on 2008-07-24
I've got a Sony Vaio VGN-NR498E and i can't seem to change the screen brightness.
The Graphics is some Intel Card

---

### Post by T2manner on 2008-07-24
help please

---

### Post by T2manner on 2008-07-25
./help

---

### Post by T2manner on 2008-07-26
./help

---

### Post by brntcrsp on 2008-07-27
I found instructions for my sz series here [http://doube.org/hardy-vaio.html](http://doube.org/hardy-vaio.html), but you might also want to check out [http://www.linux-laptop.net/](http://www.linux-laptop.net/) as they have lots of reviews and instructions to help with setting up Linux.

-brntcrsp

---

### Post by T2manner on 2008-07-30
I couldn't find anything, and the link you used didn't help either :\

---

### Post by w1nD on 2008-08-14
Aww darn. That site you posted said that the SPEED Mode (Nvidia 8400GS) of the Vaio SZ model doesn't support brightness! Oh well, it was worth a try. Thanks. :)

---

### Post by Daelyn on 2008-08-14
> **w1nD said:**
> Aww darn. That site you posted said that the SPEED Mode (Nvidia 8400GS) of the Vaio SZ model doesn't support brightness! Oh well, it was worth a try. Thanks. :)

If you search here in the forum, you will find others with brightness queries. it should definately support brightness. Mine does.

---

### Post by Nepherte on 2008-08-14
If you have an intel vga, you can use xbacklight to change your brightness. To install:
```
sudo apt-get install xbacklight
```

Usage:
```
xbacklight [-help]  [-display display] [-get] [-set percent] [- inc percent] [-dec percent]
```

---

