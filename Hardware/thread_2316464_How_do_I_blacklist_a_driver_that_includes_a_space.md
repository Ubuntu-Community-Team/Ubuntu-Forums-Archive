---
title: "How do I blacklist a driver that includes a space?"
date: 2016-03-08
forum: Hardware
---

### Post by tesker on 2016-03-08
I need to blacklist a driver called RALINK WLAN.  I tried in /etc/modprobe.d/blacklist.conf:

blacklist RALINK WLAN
blacklist "RALINK WLAN"
blacklist 'RALINK WLAN'

I rebooted after each attempt and this driver still continues to load.

Is there some other proper way to do this?

Thanks
Tom

---

### Post by houstonbofh on 2016-03-08
Try also;
blacklist RALINK\ WLAN

The \ means the next character is in the name, not a separator.  Done right, you can even create a file named * :)

---

