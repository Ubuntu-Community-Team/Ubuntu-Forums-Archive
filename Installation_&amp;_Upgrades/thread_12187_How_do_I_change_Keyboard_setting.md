---
title: "How do I change Keyboard setting?"
date: 2005-01-22
forum: Installation &amp; Upgrades
---

### Post by RU63 on 2005-01-22
When I installed Ubuntu i musta installed UK keyboard.  But my keyboard is a US keyboard.

How can I change it?

thx

---

### Post by Maniak on 2005-01-22
Once you are logged in you can go to Computer/desktop Preferences/Keyboard/layouts and change it there. I installed with the US keyboard but use Dvorak to type with - works well.

---

### Post by jensyt on 2005-01-22
If you're using Xorg, you can simply change your keyboard layout by editing your /etc/X11/xorg.conf file in nano (or gedit) to look like this:

```
Option "XkbLayout"  "us"
```

Actually, it's the same for XFree as well, just the file is /etc/X11/XF86Config-4

EDIT: Argh, I was posting this while the last person posted his comment...

---

### Post by RU63 on 2005-01-23
ahh, thanks guys... I ended up just adding the Keyboard Indicator to my panel then changing it in there, seems like that is the silly way of doing what Mainiak said.... As for Jensyt suggestion, this  made me look up whag Xorg was... now i found it.. and now i want to know if i i should be using that!!!! something new to learn, thanks :)

Rock on,

---

