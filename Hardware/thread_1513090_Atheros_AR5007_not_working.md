---
title: "Atheros AR5007 not working"
date: 2010-06-18
forum: Hardware
---

### Post by I Forgot My Username on 2010-06-18
I've installed Ubuntu numerous times, and everything has worked fine until now.  I reinstalled yesterday and haven't been able to use my wireless at all since.  It's not showing any networks with me 2 ft away from my router(with SSID broadcasting ON).  NetworkManager has "disconnected" under "Wireless Networks".  I looked in /etc/network//interfaces and it doesn't list wlan0 anywhere.  I can't really even tell what's wrong, it's just plain not working.  If you know of any commands I should run and post output I'd be very glad to do so.

Oh and one more thing, the specs of my laptop say I have a 5007, but "hardinfo" is reporting a 5001 instead.

---

### Post by I Forgot My Username on 2010-06-20
Turns out it was a driver problem.  I reinstalled 10 different times with a generic initrd every time and it wouldn't work, the last time I decided to try the targeted one.  That was the only difference, but it seems to have fixed everything.

Is there a way to change from general to targeted and back after installing?  What command should be used?

---

### Post by I Forgot My Username on 2010-06-22
Bump.

---

### Post by I Forgot My Username on 2010-06-25
I don't know what caused it, but it's broke again.  This is really getting irritating.  I'm ordering Vista recovery disks from my manufacturer tomorrow.

---

### Post by I Forgot My Username on 2010-07-12
Bump again.  Apparently it's fixed in 2.6.35, it's been ~2 weeks without any problems.

---

