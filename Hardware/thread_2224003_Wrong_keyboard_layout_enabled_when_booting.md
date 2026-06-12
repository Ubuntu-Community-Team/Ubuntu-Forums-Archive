---
title: "Wrong keyboard layout enabled when booting"
date: 2014-05-14
forum: Hardware
---

### Post by veddox on 2014-05-14
My laptop has a German keyboard, so I always had Ubuntu configured to use the German layout as the default when booting. As I occasionally use the standard English layout too, I kept that as a second option (under System settings -> Text entry).

It worked no problem until I recently upgraded from 12.04 to 14.04. Now I find that although the icon in the task bar tells me that I'm using the German keyboard after booting, it is the English layout that is actually enabled. It doesn't take much time to switch back to the German, but it is a bit of a nuisance...

Does anybody know how to set the system up so that it automatically uses the German layout?

---

### Post by keratos2 on 2014-05-14
dpkg-reconfigure xkb-data

---

### Post by veddox on 2014-05-14
What does that do?

---

