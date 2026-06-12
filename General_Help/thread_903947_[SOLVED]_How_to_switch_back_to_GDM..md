---
title: "[SOLVED] How to switch back to GDM."
date: 2008-08-28
forum: General Help
---

### Post by nerd0795 on 2008-08-28
Well recently I wanted to try KDE4 so I installed Kubuntu desktop on my current Ubuntu install.  I ended up selecting use KDM.  I found out I really wasn't too impressed with KDE so I decided to uninstall.  Now when I start up the computer it ends up in a text based log in window.  I have to type startx  to start it up.  Now when I go to login Window I get this message:

> 
GDM (Gnome Display Manager) is not running:
You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or XDM. If you wish to use this feature, then your system will need to be configured to use GDM instead.


How can I switch back to GDM?

---

### Post by SunnyRabbiera on 2008-08-28
reinstall GDM, that is what worked for me.
sudo apt-get install gdm

---

### Post by nerd0795 on 2008-08-28
It didn't work.

---

### Post by SunnyRabbiera on 2008-08-28
well you can also reinstall kdm too, but this time when it asks you to switch select GDM.
after that remove kdm again.

---

### Post by nerd0795 on 2008-08-28
What terminal code do I use?

---

### Post by nerd0795 on 2008-08-28
Actually I ended up typing in a code I got from another website and this is what terminal says:

> alex@alex-desktop:~$ sudo dpkg-reconfigure gdm
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.


---

### Post by nerd0795 on 2008-08-28
I rebooted and it instantly went to the login GUI so I guess it did that while rebooting.

---

### Post by whitefort on 2008-08-29
> **nerd0795 said:**
> Actually I ended up typing in a code I got from another website... sudo dpkg-reconfigure gdm

This problem has been driving me nuts, and I'd pretty much reconciled myself to waiting until the next Ubuntu release to get it fixed.  But this command did the trick.

MANY thanks for sharing!!

---

