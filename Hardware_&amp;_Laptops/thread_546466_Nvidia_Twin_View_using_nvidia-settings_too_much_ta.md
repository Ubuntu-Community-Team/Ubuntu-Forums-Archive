---
title: "Nvidia Twin View using nvidia-settings too much taskbar"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by sparckis on 2007-09-08
Hello,
     I'm using a dell e1705 laptop with an nvidia card.  In the past, I have used the command nvidia-settings to setup twin view mode on my laptop.  The layout showed the taskbar/panels on one screen only.  Then I could just drag a window to the next space if I ever needed it.  If I opened a window, it would either open on one or the other screens, but one screen only.

     Now, i have something screwed up somewhere.  The panels stretch across both screens.  Also, opening a new window opens it in the middle of the two screens.  Ack!  Also, maximizing a window stretches it across both screens.  

Does anyone have any clue how I'm supposed to get this back to normal?  I have the nvidia-glx-new driver.

Thanks

---

### Post by zbot on 2007-09-16
Hi,

Check your xorg.conf file (located at /etc/X11/xorg.conf)

It seems that if you are using "separate X screen" mode, you might have disabled "xinerama" which is what allows you to have two separate screens as opposed to one large one.

Look for the lines:

[code]
Section "ServerFlags"
Option         "Xinerama" "1"
EndSection
[\code]

And make sure Xinerama is set to 1 (i.e. true)

Cheers,
-Cisco (zbot)

---

### Post by sparckis on 2007-12-09
Hi,
     Somehow I got this working on Fiesty but now I am on gutsy and I have the same issue.  I've changed Xinerama to 1 in the xorg.conf file which seems to have no effect.  When I reboot this machine, it still stretches it across both monitors and opens windows in the middle.
     I've read about this alot online with people wanting to do exactly what I want to do.  Some articles even say that it just starts to work by "magic" (multiple reboots).  Is there something that I am missing to get this to work?  Is there any push to make nvidia-settings better for this problem?

Thanks

---

