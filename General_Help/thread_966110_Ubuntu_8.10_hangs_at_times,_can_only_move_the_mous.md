---
title: "Ubuntu 8.10 hangs at times, can only move the mouse."
date: 2008-11-01
forum: General Help
---

### Post by warrentang on 2008-11-01
Hi, 

This is the first time I use Ubuntu, and [I've just installed Ubuntu 8.10 which dual boots with Windnows XP on my DELL D610 laptop]("http://ubuntuforums.org/showthread.php?t=964572"). 

However at times the system hangs, and I can only move the mouse but nothing else is responsive. I have to hard reset the machine, which is quite unacceptable. 

After several times I guess it might be related to WiFi. For the hangs usually happens when I am accessing the internet, for example when I use IM, or Firefox. 

Another possible cause might be the Video Card Driver. I am using ATI Mobility X300. And Ubuntu asked me to install some drivers but when I went on it just failed without error message (an empty message box with a cross mark and an empty string).

Have anyone encountered such problems? What shall I do to solve it? 

Regards,
Warren

---

### Post by Chayak on 2008-11-01
Same issue here, I'm running it on a Lenovo T60 with an ATI mobility graphics chip which hasn't had any issues in the past with linux.

---

### Post by TopBanana on 2008-11-03
Same issue here.  I have a Dell Inspiron 9400 with an ATI Mobility X1400.  I see a trend emerging...

Mine also failed to install the ATI drivers without any error being shown.

---

### Post by Jinja on 2008-11-05
Same for me. With an Acer Aspire 1680 with Ati 9700/64mb - at first i got ubuntu installed and got the problem, but after trying reinstall Ubuntu twice, I can't even install Ubuntu because after choosing language and a single click on the next bottom, the mouse begins lag and i can't do anything.

---

### Post by Kazur on 2008-11-08
Same thing happens to me. Nvidia 8800GT, 8GB ram, 64Bit. Intel Core2Duo CPU. I've been using Ubuntu since 6.04/6.10, and I've never experienced this before. I hope someone has a solution. I don't have to reboot, CTRL+ALT+Backspace (X-restart) is enough. Happens 2-10 times a day. Wired internet connection if that matters.

---

### Post by RobOrr on 2008-11-08
I have this error running 8.04, and only once I've activated firefox at some point since i turned the machine on. No solution has been found as yet, and it's only happened to me since the kernel update of 8.04. however, 8.10 uses a different kernel (27 rather than 24) so either our problems aren't the same, or its not the kernel that's involved. My ATI card gave me a lot of grief, but I eventually managed to get it working. I tried pretty much every method available here, and due to the perpetual fog in my memories I cannot remember which one worked, sorry:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Kazur on 2008-11-08
I've noticed that it often happens when I'm running VirtualBox, though that's not always the case.

---

### Post by Jinja on 2008-11-10
Now i have tried openSUSE 11.1 Beta 4 with the same outcome hangs when i try install it.

---

### Post by RobOrr on 2008-11-11
It has been fixed for me by  upgrading to 8.10 with latest updates, so it seems for me the problem had something to do with the kernel.

---

