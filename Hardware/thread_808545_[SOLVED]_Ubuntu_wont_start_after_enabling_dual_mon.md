---
title: "[SOLVED] Ubuntu wont start after enabling dual monitors"
date: 2008-05-26
forum: Hardware
---

### Post by The Spy on 2008-05-26
Okay, I just wanted to see what dual monitors looked like in Ubuntu, since I heard that 8.04 was supposed to have better multi monitor support.

I plugged my Dell CRT monitor into my Powerbook g4 laptop using an VGA adapter; enabled dual monitors, then had to log out to finish the configuration. But now I can't even get to the login screen.

I'm needing help disabling the dual monitors without being able to access the GUI.

---

### Post by Nexano on 2008-05-26
ctrl+alt+f1
login
cd /etc/X11
ls
if theres a file named xorg.conf~ or xorg.conf.bak or xorg.conf.backup - sudo cp xorg.conf-whateverthelastpartwas xorg.conf
sudo /etc/init.d/gdm restart

---

### Post by The Spy on 2008-05-27
Hey man thanks. I'll have to remember this one.

Have you been able to get a dual monitor setup? If so how did you do it?

---

