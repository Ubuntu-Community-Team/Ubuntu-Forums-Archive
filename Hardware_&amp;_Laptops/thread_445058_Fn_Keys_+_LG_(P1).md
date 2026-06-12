---
title: "Fn Keys + LG (P1)"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by uterrorista on 2007-05-15
Only **sound** and **brightness** Fn keys work in my LG P1.

Does anyone knows out to put the rest of the Fn Keys  to work??
any kind of clue?

Thanks

---

### Post by nachotronics on 2007-05-16
Hello, try this:
```
sudo gedit /etc/modprobe.d/blacklist
```
And add the following line at the end of that file:
```
blacklist video
```

That fixed my brightness control functions. Better than nothing...

Hope this helps :wink:

---

### Post by uterrorista on 2007-05-18
thanks, but... that is already working!

---

### Post by nachotronics on 2007-05-18
Did you try to cofigure them going to System - Preferences - Key combinations??

or else you can try keytouch
```
sudo apt-get install keytouch
```

It lets you configure the media keys, and other functions

---

