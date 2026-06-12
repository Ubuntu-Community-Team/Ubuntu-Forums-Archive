---
title: "3-monitor setup broken after upgrade (&quot;Could not set configuration for CRTC&quot;)"
date: 2013-11-04
forum: Hardware
---

### Post by Scrivs on 2013-11-04
Hey all!

I'm using a Thinkpad T430 with Intel HD4000 graphics. I use this computer with a Thinkpad dock/port replicator, through which I've had a 3-display setup including the laptop's own display and two external DVI displays. I recently upgraded from Ubuntu 13.04 to 13.10, and suddenly one of the displays quit working with the error "Could not set configuration for CRTC65". Thinking it might have been doing this because I simply did an in-place upgrade, I did a fresh reinstall of the O.S., but no dice. Also, it is not always the same monitor that is disabled -- sometimes it decides it wants to use the other instead, as long as both are connected.

This problem I'm having sounds similar or identical to these:

[http://askubuntu.com/questions/195812/2-external-displays-on-thinkpad-t430s-with-hd4000-graphics](http://askubuntu.com/questions/195812/2-external-displays-on-thinkpad-t430s-with-hd4000-graphics)

[http://askubuntu.com/questions/94196/problem-with-3-monitor-configuration-2-monitors-and-a-tv](http://askubuntu.com/questions/94196/problem-with-3-monitor-configuration-2-monitors-and-a-tv)

These both claim that a 3-display setup is not feasible in Ubuntu, but this cannot be -- I had a flawless 3-display setup with no special configuration needed under 13.04. Why not 13.10?

Let me know what I need to do to provide you with information on this issue. Til then I'm sitting at work with one dead monitor, which hampers productivity a bit in my case.

---

### Post by Scrivs on 2013-11-11
Bump -- it's been one week, issue persists.

---

### Post by jp734 on 2013-11-12
Have you looked for some clues on your log files /var/log?

---

### Post by benbeecher on 2013-12-23
I've had the same experience with the same hardware on Debian - I'm wondering if it's kernel related?

---

### Post by johannes4 on 2014-02-07
Hi, did you solve the problem? I had the same problem after upgrading from 13.04 to 13.10. Now I rebooted and chose an older kernel version and I can use all three monitors again.

---

