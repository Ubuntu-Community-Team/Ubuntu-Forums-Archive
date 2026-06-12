---
title: "cursor jumping and random text insertion on MacBook Pro"
date: 2011-08-05
forum: Hardware
---

### Post by dr_chad on 2011-08-05
Hello,

I have Ubuntu 11.0.4 installed on my MacBook Pro Duo-Core, and it is
working great, except for a very annoying bug.  No matter what desktop
I use, KDE, Gnome Classic, Unity, Gnome 3, etc, or what editor I used,
gedit, tying email in gmail inside firefox, vi, etc, the cursor jumps
randomly to another location and then inserts random bits of text,
from a few characters to sometimes 3 or for sentences.  If I have
copied something recently, then it whatever was in the buffer last
often gets inserted at wherever the cursor jumps to.  I use Ubuntu for
scientific research, and must edit documents all the time, as well use
multitude of terminals.  The cusor jumps so often, I can typically can
only type 3 to 5 characters before it jumps someplace random and
inserts random text.  It is really slowing me down and taking 8 to 10
times longer to edit documents, write programs and compose emails.

I have done extensive searches online.  Many articles seem to think
its related to the touchpad, but I am extremely careful not to touch
the touhpad, and use an external USB mouse.  But, still it happens.
Also, if it was cursor jumping without the random insertion of text, I
could accept that perhaps I was bumping the touchpad.  But, why does
it insert random bits of text.  Since it happens across every KDE,
Gnome Classic, Unity, Gnome 3, etc., on every type of editor, from
terminals, to gedit, to gmail, the problem must be be a lower level
problem, with either the kernel or the X11.

I found these article:
[http://radu.cotescu.com/how-to-fix-cursor-jumping-in-ubuntu/](http://radu.cotescu.com/how-to-fix-cursor-jumping-in-ubuntu/)

[http://www.rvdavid.net/disabling-the-laptop-touchpad-in-ubuntu-linux/](http://www.rvdavid.net/disabling-the-laptop-touchpad-in-ubuntu-linux/) 



The first article provides three different solution.  The last solution is no
longer available through apt-get.  I tried the first method, and it
did not work.  I have not tried the second solution.  Also, why in the
Unbuntu control panel for the touchpad is there no way to competely
turn off the touchpad, or to turn it off when an external mouse is
plugged in?  Both of these options should be added to the control
panel for the touchpad.

From the second article, I was able to get the touchpad to turn off and on using **synclient TouchPadOff=1**, after modifying the xorg.conf file as specified in the article, but still having troubles.

Instead of manually turning off the touchpad, is there a way to turn the touch pad on off and off automatically whenever an external mouse is plugged in?

Could you please offer some advice or help here.  I really do NOT
think it is a touchpad issue.  I am NOT bumping the touchpad.
Sometimes it happens when my fingers are not even on the keyboard or
anywhere near the touchpad.... unless there a weird bug in the driver
for the MacBook touchpad that causes this, regardless of whether it is
bumped or not.


Many Thanks,

dr_chad

---

