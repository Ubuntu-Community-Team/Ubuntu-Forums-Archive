---
title: "Cannot start new display, perhaps X-server is not configured properly"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by electronic spark on 2009-02-26
Every time I try to switch user, I get a problem it displays Cannot start new display perhaps it is not configured well

I searched on google and came up with sudo dpkg-reconfigure xserver-xorg
First question I answered Y, and the rest of them default (Enter)

After I rebooted it was scanning my 500gb drive, however it was taking forever (~ 1 hr) it was only displaying Not optimised screen resolution, should be 1280 x 1024 scrolling around my screen, so I did ctr-alt-backspace, it went to shell, from there I did ctr-alt-delete and it shut down.  Multiple restarts and retries didn't work and I still can't log on into my desktop.

I use ubuntu 8.10 with all updates, ati pro 128 video, same issue was in my laptop running Mint 6.0, ati-radeon when trying to switch user, but if I tried switch user again, it worked second time.

If I start in recovery mode how do I fix the xserver resolution? problem?

---

### Post by zspider on 2009-04-16
This happened to me on linux mint 6. upon attempting to switch users it would say "Cannot start new display perhaps it is not configured well" then it would go away and every 7 days the xserver would glitch out [the screen would become garbled including in the virtual terminals] requiring a total restart of the machine i had to stop using mint because it kept happening.

---

