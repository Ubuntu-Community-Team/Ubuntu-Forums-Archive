---
title: "Lenovo Yoga 900 - Touchscreen &amp; Touchpad not working"
date: 2015-12-25
forum: Hardware
---

### Post by babu98712 on 2015-12-25
Hi, I am new to Ubuntu (and Linux pretty much) I bought a Lenovo Yoga 900 for a new laptop, but when I saw how ugly everything looked on Windows 10, I decided I should just move to Ubuntu. Right now, I am using Ubuntu Gnome 15.10. What is working is the Wireless Connectivity, Webcam, Keyboard, USB Ports, though the only things that are not working is the touchscreen and touchpad! I looked at some forums, but they were to complicated to understand. If anyone can find an answer, please try to be as simple as possible. Thanks.

---

### Post by reheatedcake on 2016-01-06
Hey! Fellow Lenovo 900 user here! I found that compiling the 4.4.0 kernel from [https://github.com/torvalds/linux/](https://github.com/torvalds/linux/) fixed my trackpad and touch screen

I used [this guide]("http://www.cyberciti.biz/faq/debian-ubuntu-building-installing-a-custom-linux-kernel/") to make the .deb packages but instead of doing sudo dpkg -i linux-headers.deb I just installed them through software center

All the changes you'll find here: [https://bbs.archlinux.org/viewtopic.php?pid=1579194#p1579194](https://bbs.archlinux.org/viewtopic.php?pid=1579194#p1579194) are already in the 4.4 kernel

Unfortunately, like the fellow on the arch forums, my touchpad (but not touch screen) fails after I suspend or shut the lid. Restarting/logging out and logging back in fixes it though

edit:

Pressing control-alt-f2 followed by control-alt-f7 fixes it!

---

### Post by babu98712 on 2016-02-20
Hi, thanks for the info, but it looks like I found this and actually fixed this. A long time ago. Maybe Jan. 1. But yes, thanks for the reply anyway. I still have the problem with suspending, because after suspend, doing Ctrl-Alt-F2 and then Ctrl-Alt-F7 only enables the touchscreen. Though, thanks for the info. I'm going to mark this as solved (If I know how.)

---

