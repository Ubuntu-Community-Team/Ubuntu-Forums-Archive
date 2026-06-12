---
title: "VGA driver can't be installed bcuz of an X-Server!!!"
date: 2009-01-18
forum: Hardware
---

### Post by James4 on 2009-01-18
recently I downloaded my VGA driver(nVidia FX5500) and tried to install it using "sh" command but it says there is an x-server running on my pc though it can't be installed.
how can I disable the x-server?

---

### Post by jfr1tz on 2009-01-18
Via the console by calling gdm(sudo /etc/init.d/gdm stop)  or booting into rescue mode and then choose to boot into a shell( dont know how it's labeled exactly).

Are you trying to install an older binary driver for the nvidia card and/or is the builtin nvidia driver not working? because manually installing nvidia drivers this way can interfere with the system and might leave you without a working x server at all( you want a working x-server ;).

---

### Post by James4 on 2009-01-20
oh what a fool I am..
I tried the auto driver installer while I wasn't conncted to the internet and wondered why it is not working?!
thanks dude...
everything is ok now...

---

