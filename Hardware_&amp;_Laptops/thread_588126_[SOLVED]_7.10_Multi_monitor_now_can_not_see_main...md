---
title: "[SOLVED] 7.10 Multi monitor now can not see main..help"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by dutchbo2 on 2007-10-23
I was trying to setup an external monitor from my laptop with gutsy 7.10.
Thought I had set and it asked me to restart when I did my laptop monitor came up black. Now I can not see to fix problem. How do I get my laptop monitor back?? !!!

Thanks
Bill

---

### Post by bogoliubov on 2007-10-23
Let it boot, then when you think it has finished, hit Ctrl-Alt-F1 to get a console. Log in.

Then we can se what xrandr thinks about the situation. Do:
xrandr -q
And show us the output....


Also we can have a look at what files are available in /etc/X11/. Do:
ls -l /etc/X11
And show us the output...

Hopefully the displayconfig-program should have made a backup of you old xorg.conf. If so, we need only to copy the backup file to the original one.

---

### Post by dutchbo2 on 2007-10-23
Tried it but I can still not see anything. I think it changed the resolution or the driver type of my laptop instead of the external monitor. Any other ideas? Anyone?

---

### Post by bogoliubov on 2007-10-24
Do you still have the LiveCD? In that case you can boot the LiveCD. If you have, like I mentioned earlier, a backup file of xorg.conf then we can copy it back! 

Probably the backup xorg.conf is called xorg.conf.1 or .2 and so on..., at least if you've been using the displayconfig-gtk program. 
But perhaps it's not necessary to copy back the backup, perhaps we can just edit xorg.conf!

Please note that when you run the LiveCD, your xorg.conf on you installed system will of course no be in /etc/X11. It should be on another disc. When you boot the LiveCD type "mount" and "df -h" to get a hint on where you installed system is...

---

### Post by dutchbo2 on 2007-10-25
Fixed problem.
esc at startup
started in recover mode and entered my root password.

Then ran following

sudo dpkg-reconfigure xserver-xorg

Followed prompts and questions and restarted.

Monitor came back to life.

---

