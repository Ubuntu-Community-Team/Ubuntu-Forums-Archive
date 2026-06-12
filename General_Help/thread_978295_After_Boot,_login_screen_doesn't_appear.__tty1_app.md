---
title: "After Boot, login screen doesn't appear.  tty1 appears"
date: 2008-11-11
forum: General Help
---

### Post by zkaiwen on 2008-11-11
I have just recently installed Ubuntu 8.10 on my Fujitsu t4220 tablet PC. Everything was working fine. I even restarted it a couple times with no problems. However, now, it seems I can't log on to the desktop part of Ubuntu. After the initial boot, it takes me to tty1 and asks for log in and password. How do I boot into the graphical desktop part. Thank you

---

### Post by lisati on 2008-11-11
If you are able to login, try: ```
startx
```
This will help you know if the desktop is still startable.

---

### Post by zkaiwen on 2008-11-11
Apparently, it works. However, everytime I restart it, it takes me to tty1 still. Also, there's an error that pops up that states that there's an error with GNOME_fastuserswitchapplet.

---

### Post by unclesamslair on 2010-01-13
I have the same problem on a brand new hard drive. Same problem on previous hard drive. I am using ubuntu 9.10, except my tty1 disappears after 2-5 minutes and then the GUI starts up like normal as if nothing had happened.


Also, I dual boot karmic and vista, when my grub comes up, it has two entries for ubuntu with different version numbers, but both options dump me into the same partition and the same OS, this only happened after I updated the first time after installation. Is it a different kernel? 

How do I make it so it's less confusing to the average user and they only have two options, Ubuntu and Windows? Also, is there someway to change the colors and background in the grub to make it look nicer?

---

### Post by warfacegod on 2010-01-13
Yes those are different kernel headers. You can change GRUB rather extensively from what I understand. I'd try looking in the Installation & Upgrades section and Tutorials & Tips section. Aside from that, I don't know what advice to give you about the tty issues you guys are having.

---

### Post by warfacegod on 2010-01-14
Some instructions for GRUB2:

[http://ubuntuguide.net/manually-addingremoving-entries-to-grub-2-menu]("http://ubuntuguide.net/manually-addingremoving-entries-to-grub-2-menu")

---

### Post by john newbuntu on 2010-01-14
Some old info from Google on fastswitchapplet:
[http://ubuntuforums.org/archive/index.php/t-619767.html](http://ubuntuforums.org/archive/index.php/t-619767.html)

[http://ubuntuforums.org/archive/index.php/t-1312215.html](http://ubuntuforums.org/archive/index.php/t-1312215.html)

---

