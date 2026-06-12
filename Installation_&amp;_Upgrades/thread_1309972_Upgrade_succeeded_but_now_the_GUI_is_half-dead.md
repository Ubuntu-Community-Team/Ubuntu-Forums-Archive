---
title: "Upgrade succeeded but now the GUI is half-dead"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by EliteLegend on 2009-11-01
I had this Macintosh theme on an Ubuntu 9.04. Yesterday I upgraded to Karmic and everything was fine until I started seeing the following weird problems:

[LIST=1]
[*]Inside Eclipse, if I click on Install Software and then add a URL, it does not show me anything in the window. But if I click somewhere inside that window, I can see that there are packages being shown there but they are not visible in the window...
[*]The Gnome panels are messier than ever. They are visible until I hover my mouse over them. When I do hover my mouse, they disappear. I fixed this by killing the gnome panels and then restarting though...
[/LIST]

I tried uninstalling the Macintosh theme but that doesn't seem to help. Now, instead of troubleshooting this whole thing, is there any way I can just reinstall the whole GUI stuff?

---

### Post by unamanic on 2009-11-01
You can:
- Log off
- Press Crtl + Alt + F1
- Login in text mode
- execute the following:
```

mv .gconf bak.gconf
mv .gconfd bak.gconfd
mv .gnome2 .bak.gnome2
mv .gnome2_private bak.gnome2_private
exit

```
- press Ctrl + Alt F7
- log in and see if it's fixed

Be warned that .gconf directories hold configs for things like f-spot if you use these applications, you can selectively copy things back from the bak. directories.

---

### Post by EliteLegend on 2009-11-01
Wow... that did the trick... Everything works now... Thanks a ton!

---

