---
title: "Resolution problem"
date: 2008-10-27
forum: General Help
---

### Post by XeDoX on 2008-10-27
Hello.I'm sorry for writing this post but I'm tired of searching and testing commands which don't work(they may work,but they don't fix my problem)...I have 8800GT and I have installed the latest drivers.The problem is that I can't set the resolution to 1280x1024.The maximum allowed resolution is 1280x800 as the screenshot shows.I'll be thankful if somebody help me.

[[IMG]http://img61.imageshack.us/img61/9205/screenshotrd4.th.png[/img]](http://img61.imageshack.us/my.php?image=screenshotrd4.png)[[IMG]http://img61.imageshack.us/images/thpix.gif[/img]](http://g.imageshack.us/thpix.php)

[SIZE="1"](sorry for my English,I'm still studying it)[/SIZE]

---

### Post by jeyaganesh on 2008-10-28
Try the following command in terminal

sudo dpkg-reconfigure xserver-xorg

Then follow the screen instruction. It will ask key board layout and screen resolution one by one. If you find your exact screen resolution select and finish.

Then restart the X-window, by pressing Alt+Ctrl+back space. It will ask you to enter username and password. See if you can select your desired resolution in the settings.

I fixed my resolution problem using that command.

---

