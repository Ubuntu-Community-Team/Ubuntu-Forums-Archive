---
title: "Vaio VGN-NR contrast adjustment not working"
date: 2009-02-20
forum: Hardware
---

### Post by uberlinux on 2009-02-20
> Hi Everyone,

So I made the mistake of buying a Vaio without knowing that the bios is EFI and unavailable outside of the OS tools for it.  (Phoenix TrustedCore)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173652)
I've done a lot of reading, and tried a lot of things with fsfn, screendimmer, etc, and nothing's worked.  

The brightness is stuck at full, and while the function buttons for contrast go up and down, they don't affect it. 

Has anyone found a way around this?

Thanks,
 - Kodiak

UPDATE:  Found these links with more info:
[http://ubuntuforums.org/showthread.php?t=465491&page=1](http://ubuntuforums.org/showthread.php?t=465491&page=1)
[http://club.vaio.sony.eu/clubvaio/gb/en/forum/viewthread?thread=54628](http://club.vaio.sony.eu/clubvaio/gb/en/forum/viewthread?thread=54628)
[http://www.eltan.com/tcbios.htm](http://www.eltan.com/tcbios.htm)

My solution that works most of the time:
( From this bug report:  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173652) )

> Then add these 2 lines to /etc/rc.local (or just execute from the command line):

xrandr --output LVDS --set BACKLIGHT_CONTROL native
/etc/init.d/acpid restart

And edit /etc/acpi/sonybright.sh so that is contains only this:

#!/bin/bash
if [ "x$1" = "xdown" ]; then
   xbacklight -time 100 -steps 10 -dec 10 2>/tmp/sonybright.log
elif [ "x$1" = "xup" ]; then
   xbacklight -time 100 -steps 10 -inc 10 2>/tmp/sonybright.log
else
   echo >&2 Unknown argument $1
fi

---

### Post by uberlinux on 2009-02-21
SOLVED, or at least, worked around.  Details shortly.

EDIT:  not solved.  Posing below.

---

### Post by uberlinux on 2009-02-21
So the above method shows that the Vaio w/ x3100 gfx can be controlled; but now the brightness seems to fade between perfect and too dim, every few minutes, and the brightness apps become non-responsive.  This is driving me crazy.  

Finding a permanent fix is now worth  $30 to me.  Anyone got an idea to make the brightness control work stabily?

---

### Post by uberlinux on 2009-02-21
> **uberlinux said:**
> So the above method shows that the Vaio w/ x3100 gfx can be controlled; but now the brightness seems to fade between perfect and too dim, every few minutes, and the brightness apps become non-responsive.  This is driving me crazy.  

Finding a permanent fix is now worth  $30 to me.  Anyone got an idea to make the brightness control work stabily?

Trying another lead from this thread that describes *EXACTLY* what's going on on mine.

[http://ubuntuforums.org/showthread.php?t=972323&highlight=X3100](http://ubuntuforums.org/showthread.php?t=972323&highlight=X3100)

---

