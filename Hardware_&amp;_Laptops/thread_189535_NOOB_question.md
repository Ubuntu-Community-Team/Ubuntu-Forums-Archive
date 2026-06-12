---
title: "NOOB question"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by AlexBryan on 2006-06-05
OK this is probably very very easy to answer. I have a blank screen at login, I read this post on how to fix it:

"Now this problem was also in breezy and is quite imoportant:
After the installation, when the X first starts the screen is blank. (i can hear the sound produced by the login screen) but no image is shown.
The only way i could fix this is CTRL+ALT+F1 -> login -> edit xorg.conf file in this way:
on the Section "Device" i have to add this line:
 Option "MonitorLayout" "LVDS,Auto"
then save the file and restart X."

So I press Ctrl+Alt+F1 and get the command promt:
ubuntu@ubuntu:~$
The next step is to login, HOW do I login?
This is the first time I've used linux and I'm boot off the live CD.
Cheers

---

### Post by nolongerlivecd on 2006-06-05
If i'm not wrong, it should be logged in already

---

### Post by AlexBryan on 2006-06-05
Thanks for the reply.
I'm confused. How do I edit the xorg.conf file from this command promt?

---

### Post by nekr0z on 2006-06-05
Just do this:

sudo nano /etc/X11/xorg.conf

The "nano" editor with xorg.conf opens. You just edit what you need, and then press CTRL+X to exit, saying Y when asked to save file.

I would also advise making a backup before editing:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

so that you can always restore the file if you do something wrong. Restoring would be:

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

---

