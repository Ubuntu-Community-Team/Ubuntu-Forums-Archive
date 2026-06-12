---
title: "Dead Battery Notification"
date: 2010-05-03
forum: Hardware
---

### Post by techunit on 2010-05-03
Alright. I know that my battery is dead/half depleted but I don't want a update on its capacity every time I log in. Is there a way I can get around this problem. I am sure there is some way of doing it but I would like the advice of those who would like to help. Thanks...

](*,)

---

### Post by jerrrys on 2010-05-03
open up power management found in system/preferences and...[ATTACH]155387[/ATTACH]

---

### Post by techunit on 2010-05-03
thanks I will take a look at that... I didn't find anything in there earlier but I hope I just didn't see it....

---

### Post by techunit on 2010-05-03
This is not what I mean... I get a pop up notification that warns me about the battery being being dead.

---

### Post by kgarbutt on 2010-05-03
Open up your terminal and paste this line in at the command prompt:

gconftool-2 --set /apps/gnome-power-manager/notify/low_capacity --type bool 0

hit the return key and you are good to go.

Ken

---

### Post by jerrrys on 2010-05-03
nevermind...

---

### Post by techunit on 2010-05-03
> **kgarbutt said:**
> Open up your terminal and paste this line in at the command prompt:

gconftool-2 --set /apps/gnome-power-manager/notify/low_capacity --type bool 0

hit the return key and you are good to go.

Ken

Now I wan't to know when my computer is low on battery power but the annoying message about how the battery is dead should go away yes? Well Why am I asking this because I can fix it pretty easy if I doesn't do what I wan't..

---

### Post by techunit on 2010-05-03
Great Thanks Alot KGARBUTT...

---

