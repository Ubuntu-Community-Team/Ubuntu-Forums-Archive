---
title: "cups problem &quot;Unable to bind socket for address...&quot;"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by chilly_willy2 on 2006-01-05
I have a Samsung ML-1740 which works nicely with Linux.  I'm using Kubuntu with KDE 3.5 and cupsys 1.1.23-10ubuntu-4 on kernel 2.6.12-10 stock.  When I try using the KDE System Tools -> Printers tool, it hangs for a while then stays on "Initializing manager" window until I xkill it.  I also installed gnome-cups-manager, but it wouldn't even start.  I tried going to localhost:631, but it said it couldn't be found.

When I restart cups (/etc/init.d/cupsys restart), everything says it's fine, but still nothing works.  When I checked the logs in /var, it said it couldn't find /etc/cups/printers.conf or /etc/cups/classes.conf, so I copied both of those over from /usr/share/docs/cupsys/examples. Still, cups daemon restarts fine, but no printer managers loads.

I think this line is the culprit, but I can't find out what it means:
"StartListening: Unable to bind socket for address 7f000001:631 - Cannot assign requested address."
I've tried netstat -tlnp and nothing is using port 631.  Any ideas?  Thanks!

---

