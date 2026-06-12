---
title: "Resolution troubles..."
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by camokale on 2005-05-09
Hey, I'm a disgruntled Windows User looking to meander to the world of linux.  I'm really impressed with Ubuntu's ease of use, but I have a problem: my display is stuck at 640 x 480.  Ugh!  My display card is an Intel 82845G/GL/GE Graphics card and a Dell LCD monitor that supports up to 1024 x 768 pixels (which I prefer).  I've read some posts on how to edit the /etc/x11/xorg.conf file, but it says it is a read-only file and I can't edit it.  Any ideas?

---

### Post by Professor X on 2005-05-09
In order to have write access to /etc/X11/xorg.conf, you need to edit the file using sudo.  The complete command is ```
sudo gedit /etc/X11/xorg.conf
```.  The rest is explained clearly in [this post](http://www.ubuntuforums.org/showthread.php?t=33072)

---

### Post by camokale on 2005-05-09
Yep, I did exactly that.  It opens up gedit with a blank page.  Same with Kate and all other text editors.  I pressed "save" for the hell of it and it still said "Can not save file."
???

---

### Post by Professor X on 2005-05-09
[QUOTE=camokale]Yep, I did exactly that.  It opens up gedit with a blank page.  Same with Kate and all other text editors.  I pressed "save" for the hell of it and it still said "Can not save file."
???[/QUOTE]
 Does the file exist?  (ls /etc/X11/xorg.conf)

---

### Post by DutchLau on 2005-05-09
I have the same exactly problem.. :mad:  (I have alot of problems - 3 completely different computers running Ubuntu)

I blew up one of my monitors yesterday (17 inch) and I put a 15 inch monitor in its place for the meantime. Now it's stuck on 640x480 (I can't change in the display resolution, so I'll check this out when I'm on that computer again - first I'm going to compile that kernel!). Thanks prof. X!

DutchLau

---

### Post by poofyhairguy on 2005-05-09
[QUOTE=camokale]Yep, I did exactly that.  It opens up gedit with a blank page.  Same with Kate and all other text editors.  I pressed "save" for the hell of it and it still said "Can not save file."
???[/QUOTE]


It are you sure you copied the command correctly? On letter off and.....

(I do it sometimes)

---

### Post by camokale on 2005-05-09
Well, I got it figured out.  It turned out I typed x11 instead of X11.  I didn't know capital letters counted.  BUT sadly, that was not what fixed my resolution woes.  I simply reinstalled Ubuntu and a strage box popped up during setup that asked what resolution I would like to use ????!!!!  It's worked fine since, I'm running KDE now.  Thanks all who put up with noobs...

---

### Post by poofyhairguy on 2005-05-12
[QUOTE=camokale]Hey, I'm a disgruntled Windows User looking to meander to the world of linux.  I'm really impressed with Ubuntu's ease of use, but I have a problem: my display is stuck at 640 x 480.  Ugh!  My display card is an Intel 82845G/GL/GE Graphics card and a Dell LCD monitor that supports up to 1024 x 768 pixels (which I prefer).  I've read some posts on how to edit the /etc/x11/xorg.conf file, but it says it is a read-only file and I can't edit it.  Any ideas?[/QUOTE]

Thats not he way to got about it (no offense, it was good idea). The fix to the problem should be here:

[http://www.ubuntuforums.org/showthread.php?t=30235&page=2&pp=10](http://www.ubuntuforums.org/showthread.php?t=30235&page=2&pp=10)

---

