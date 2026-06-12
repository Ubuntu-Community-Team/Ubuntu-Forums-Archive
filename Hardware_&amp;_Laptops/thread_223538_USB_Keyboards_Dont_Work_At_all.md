---
title: "USB Keyboards Dont Work At all"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by maddog39 on 2006-07-26
Hello all,

I am having serious issues with USB keyboards, I have tried over 3 keyboards and none of them are detected by ubuntu, or any other linux distro except for Linspire. They are standard 102 key keyboards and are USB 2.0 compatible. I burned out my PS/2 ports overlocking so my other keyboards which used to work wont work anymore. Anything I can do?

Thanks!
-maddog39

---

### Post by Ziox on 2006-07-26
i'm sure you have tried dpkg-reconfigure xserver-xorg right? ;) anyhow it has to do with your xorg.conf, so can you post it here? its located at /etc/X11/xorg.conf

---

### Post by Euphoric Invasion on 2006-07-26
I read this and thought, since not all hardware works with all linux distro, and since it did work under Linspire, maybe ubuntu cant recognize those particular usb keyboards.  It might require extra configuring or even a driver-like program for ubuntu.  one of my friends has a usb keyboard with slackware linux and it works just fine, so maybe its just those keyboards.  if you can, try them on a windows xp computer and see if it recognizes them.  maybe they are bad or maybe the usb connectors on the computer are bad.  I hope this helps you and that you are able to fix the problem.  Sorry i couldnt be of any more help.

---

### Post by maddog39 on 2006-07-26
Well I currently use one of the keyboards on Windows XP and it works just fine, all of them do and they dont need drivers either. Also I cant try xorg-reconfigure because I cant type anything so theres no way for my to get there. Also the keyboard works all the way up until the point where GNOME starts to load, then it goes dead.

[Edit]
I cant even get Ubuntu to install. :/

---

### Post by cracker on 2006-07-27
If your keyboard works during the console mode, I'd recommend using the advanced CD and not loading X automatically. This way, you can try different solutions, then start X manually to test, and once you find the solution, you will be able to install properly. This is most likely just a configuration issue, and should be an easy fix.

---

