---
title: "Mouse Questions in Gnome"
date: 2008-11-05
forum: General Help
---

### Post by Arkhar on 2008-11-05
Hey all - Running Ubuntu 8.10 64bit w/ Gnome and I had some questions/issues about my mouse.


My back and forward side buttons work in Firefox, but not in my file browser (nautilus). I was wondering if there was a way to get that to work.

Also I wanted to try to get the scroll button working in Firefox. The scrolling works just fine but I was wondering if it was possible to use the scroll button click to do autoscroll like in Windows?

I've looked at the mouse setting panel under preferences but that didn't seem to help or have any features I can set. I also tried to use lomoco, but I'm not very command line savvy, and when I tried to probe for devices with it it told me all my devices were "Unsupported Logitech Devices"

I use a Logitech G15 USB keyboard and a Logitech MX600 Wireless USB Mouse.

Thanks in advance for any help anyone can offer!

---

### Post by Arkhar on 2008-11-08
No help with this? 

:(

---

### Post by Raouf on 2008-11-08
> **Arkhar said:**
> 
Also I wanted to try to get the scroll button working in Firefox. The scrolling works just fine but I was wondering if it was possible to use the scroll button click to do autoscroll like in Windows?


It's a Preferences on Firefox not on your mouse

Just Start your Firefox
View> Preferences> Advanced
Select "General" Tab
then in Browsing Section, Click on "Auto Scrolling"
give a try now :D
sorry for my English

take care
- Raouf

---

### Post by ad_267 on 2008-11-08
This might be a bit more advanced than you need: [http://ubuntuforums.org/showthread.php?t=316441](http://ubuntuforums.org/showthread.php?t=316441)

This section looks like what you're after: 
SHORCUT: If all you want to do is set your four or five button mouse to use the extra buttons as "forward" and "back" buttons, you may have success with performing only a single action: edit /etc/X11/xorg.conf in the mouse section, and add the following two lines:
```
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"
```

Cheers for that tip Raouf, I've seen people asking about that before and never realised it was a Firefox setting.

---

