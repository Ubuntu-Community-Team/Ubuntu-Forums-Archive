---
title: "[SOLVED] Login Issues?"
date: 2008-09-01
forum: General Help
---

### Post by Hendrick on 2008-09-01
Well, I just installed Ubuntu off of the live CD.  When the system booted, it took me to the login screen.  I entered my username and password, and the login textbox, as well as the Ubuntu logo, disappears.  Then, after 3 seconds or so, the screen goes black, and the status light on my monitor goes from green to orange.  (Orange means the monitor is on, but doesn't have a feed.  Happens when Windows goes into hibernation.)

After a few seconds, the login screen reappears.  (It's not a wrong password/username error.)  I've already tried to reinstall Ubuntu, but it didn't seem to fix it.

Also, the screen resolution is really messed up.  There is about an inch or so of blackspace to the right, and a half inch or so at the bottom.  Also, a centimeter or so strip on the far left side is brighter then everything else.  I have PCLinuxOS installed, and never have experienced any of these issues before.  (Maybe it's because I have the ATI Graphics driver installed... something I haven't been able to do yet in Ubuntu since I can't login.)

Thanks.

---

### Post by schauerlich on 2008-09-01
It sounds like X is crashing when you try to log in.

---

### Post by Hendrick on 2008-09-01
How would I be able to confirm that X is crashing?  And what are the possible solutions?

---

### Post by Kurou-san on 2008-09-01
This happened to me. What you need to do is login with a Failsafe GNOME session from the login screen, and go to System -> Administration -> Hardware Drivers and check the box you see. Logout and login regularly. You should be in.

---

### Post by Sef on 2008-09-01
> This happened to me. What you need to do is login with a Failsafe GNOME session from the login screen....

To find Failsafe GNOME:

At the bottom of the login Window, click on the options box (bottom left.)

---

### Post by Hendrick on 2008-09-01
Thanks for your quick reply, however, I eventually got it a second way.

Sadly, using Windows, I downloaded and moved the ATI Linux Driver to the Ubuntu Patition.  I then booted the text based Ubuntu option from the Boot Loader, to which I selected the root terminal.  I installed the graphics driver there, and on reboot, it's working fine.

Thanks for all the quick replies though!

---

