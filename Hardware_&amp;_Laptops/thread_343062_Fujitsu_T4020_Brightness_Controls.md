---
title: "Fujitsu T4020 Brightness Controls"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by emoore625 on 2007-01-20
I just today installed Ubuntu on my Fujitsu T4020.  Gotta say I love it.  I've played around with various linux distros over the past decade but never really got into it because of driver issues.  This is the first time I've gotten mostly everything working.  With the looming cost of Vista, I figured now's a good time to find a more economical operating system.

Anyway... I digress.  I have no brightness controls on my laptop.  Volume controls work but brightness (F6 and F7) do not.  How can I fix this?

---

### Post by teaker1s on 2007-01-20
don't know your graphics manufacturer but my f6 and f7 only work with function key.

also smartdimmer installed
Change LCD brightness on Geforce 6200Go cards

---

### Post by emoore625 on 2007-01-20
I have the basic Intel graphics (either 915 or 945).

---

### Post by emoore625 on 2007-01-21
Anyone know about this?

---

### Post by Chitownguy885 on 2007-05-22
bump

---

### Post by azim.manjee on 2007-06-21
I am having the same issue on a T4020- any ideas?

---

### Post by Almostbakedyam on 2007-07-29
One way to do

```

sudo su
echo BRIGHTNESS > /proc/acpi/video/GFX0/LCD/brightness 
 
```

The BRIGHTNESS can be any number from 1 to 8.

---

### Post by tanjiajin on 2007-09-01
Instead of using terminal commands to adjust the brightness, any idea how to 'enable' the applet on the gnome panel to detect brightness settings on T4020. I've reverted to Windows thanks to the overconsumption of battery power on screen brightness. :(

---

