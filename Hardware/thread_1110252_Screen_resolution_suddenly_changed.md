---
title: "Screen resolution suddenly changed"
date: 2009-03-29
forum: Hardware
---

### Post by Jason32 on 2009-03-29
Today I plugged my laptop into an external monitor for a little while, and when I disconnected it the native resolution of my laptop screen is no longer available as an option.

I have a Dell Inspiron 1300 which has a screen resolution of 1280x800 and previously this was working fine, but now 1024x768 is the best resolution available in the display resolution preferences.

How do I get my resolution back?

---

### Post by Jason32 on 2009-03-29
OK, I managed to fix it myself by running
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Can anybody tell me why that was necessary? I don't understand.

---

