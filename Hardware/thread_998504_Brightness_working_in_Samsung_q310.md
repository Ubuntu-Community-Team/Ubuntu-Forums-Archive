---
title: "Brightness working in Samsung q310"
date: 2008-11-30
forum: Hardware
---

### Post by Jophish on 2008-11-30
I have managed to get the display brightness working in a Samsung q310. Using this script: 

```
  chvt 1
  echo -n 10 > /proc/acpi/video/NVID/LCD/brightness
  chvt 7;;
```

Now, how hard would this be to integrate system wide, so I could change it, for example, using the gnome applet in the top bar?

Credit for the script goes to ideefixe123 of the nvnews forums. My thanks to him.

---

### Post by davbren on 2008-12-30
Ok I got it to work by puttin this into a .sh file and running that through the terminal. So thats all good. 

Problem is that I always end up at a text entry screen. no gdm or anything. The brightness is less though. Which is great :D

---

