---
title: "[SOLVED] &amp;quot;OUT OF RANGE&amp;quot; Monitor problem?"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by seoras on 2005-09-23
I've been running Ubuntu for about 2 weeks, no problems, then decided to change my monitor. Now on boot I get a blank screen with the message "OUT OF RANGE" However, if  I type my username and password 'blind' Ubuntu comes to life and my screen displays as it should. I understand this is something to do with the refresh rate of the monitor but I don't know how to fix it...any help would be appreciated.

Seoras

---

### Post by KingBahamut on 2005-09-23
Youll need to update your xorg.conf 

sudo dpkg-reconfigure xserver-xorg best way to go about this. 

Let us know how it goes.

---

### Post by seoras on 2005-09-27
Excellent !!!! kingbahamut
*sudo dpkg-reconfigure xserver-xorg* worked like a charm. There were many sections I didn't fully understand but in most cases there was a default or other oprion already chosen so I went with that. All now seems to be OK.

Many thanks
Seoras

---

### Post by coffemonkey on 2005-09-27
I had the same problem during the first install of Ubuntu. For some reason, the installer does not recognise my TFT display (DVI).
I had to use D-SUB in order to see something.

---

