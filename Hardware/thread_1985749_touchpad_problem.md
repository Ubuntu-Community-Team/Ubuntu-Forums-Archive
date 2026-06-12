---
title: "touchpad problem"
date: 2012-05-23
forum: Hardware
---

### Post by irfanh94 on 2012-05-23
Hi.

Well i have problem with the touchpad. It works on login screen, but after it stop to work.

Im using ubuntu on msi cx600 laptop, and i really dont know what to do..

---

### Post by papibe on 2012-05-24
Hi irfanh94.

What version of Ubuntu are you running?

By any chance is it 11.10? Last time I used it there was a [bug]("https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/868400").

Try opening a terminal (Ctrl+Alt+T), and try this:
```
synclient Touchpadoff=0
```
The mouse movement should return immediately. If that doesn't work, this is the other recommended solution:
```
sudo killall -u lightdm syndaemon
synclient Touchpadoff=0

```
I hope that helps, and tell us how it goes.
Regards.

---

### Post by irfanh94 on 2012-05-24
> **papibe said:**
> Hi irfanh94.

What version of Ubuntu are you running?

By any chance is it 11.10? Last time I used it there was a [bug]("https://bugs.launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/+bug/868400").

Try opening a terminal (Ctrl+Alt+T), and try this:
```
synclient Touchpadoff=0
```The mouse movement should return immediately. If that doesn't work, this is the other recommended solution:
```
sudo killall -u lightdm syndaemon
synclient Touchpadoff=0

```I hope that helps, and tell us how it goes.
Regards.

Thank You on reply but ive solved the problem. :D

---

### Post by papibe on 2012-05-24
Would you care to share it? May be it would help other users with the same problem.

Regards.

---

