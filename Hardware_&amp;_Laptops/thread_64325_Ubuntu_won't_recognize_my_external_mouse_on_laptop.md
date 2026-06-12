---
title: "Ubuntu won't recognize my external mouse on laptop"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by Jameson on 2005-09-10
I recently installed ubuntu 5.04 on my old compaq presario laptop (1600 series) when I plug in my external mouse to the ps/2 port (I think thats what it is called) it won't recognize it as being there.  The touchpad works, but I hate that thing and don't want to have to resort the that.

Any suggestions would be great.  (BTW, I am a Linux Newbie)

---

### Post by mlomker on 2005-09-10
I assume you didn't have it plugged in when you loaded the machine?  Do you have it plugged in when starting it up?  I guess it's possible that Xfree isn't recognizing and you'll have to add a section to the /etc/X11/xorg.conf file for it.  Make sure you back up that file before you edit it...errors can keep the graphical environment from loading at all.

---

### Post by Jameson on 2005-09-10
"Xfree isn't recognizing and you'll have to add a section to the /etc/X11/xorg.conf"

how do I do that? I know what Root Terminal but I don't know the commands etc.

---

### Post by cbudden on 2005-09-11
/etc/x11/xorg.conf is a config file for settings to go with the GUI.

---

### Post by mlomker on 2005-09-11
You can type **gksudo gedit** and it'll open a program similar to notepad as root so that you have permissions to edit it.

As an FYI, there's a command-line editor called **vim** that you'll want to learn at some point.  It's not what a Windows-user would consider user-friendly, though.

---

