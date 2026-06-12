---
title: "HP Pavilion Monitor Reacting Badly With NVIDIA Driver on Shutdown/Reboot"
date: 2010-12-10
forum: Hardware
---

### Post by bartlebythescrivener on 2010-12-10
[SIZE=3]  I recently installed Ubuntu 10.04 on my HP Pavilion dv9700 laptop
and have been mostly impressed.  There is one disturbing problem involving
my graphics card and monitor.  I have a NVIDIA GeForce Go 7150M graphics
adapter (apparently equivalent to nForce 630M), and have installed
NVIDIA's proprietary driver (Version 260.19.06).  NVIDIA's X-Server
Settings window identifies my monitor as a "Seiko/Epson" 1440x900.
    
The driver works fine.  But when I shut down, and the X Server
quits (a few seconds before power down or reboot), my screen begins
to look like it is frying.  Starting from the right side -- especially
the upper and lower right corners -- and moving inward, it looks as if
someone were lighting a piece of paper on fire, and it was burning to a
crisp.  This doesn't appear to be normal behavior.
    
On a lark, I attached another monitor (a Gateway FPD1760 TFT LCD)
and booted up.  It worked nicely enough (no problems with a dual monitor
set-up), and when I shut down, the Gateway monitor switched to Text Mode
while my laptop monitor did its crispy shutdown routine.  (BTW, CTRL-ALT-
Fn doesn't work for me during normal operation, it just gives a [safe]
blank screen.)
    
Anyone have an idea what's going on?  The problem appears to
be a combination of graphics adapter, monitor, and text mode.  I've been
preferring hibernation to shutdown, because it apparently doesn't
try to switch to text mode before shutting down (thus sparing my monitor).
But eventually I have to reboot in order to update my system!

    Thanks!
[/SIZE]

---

