---
title: "Suspends when unplugged"
date: 2011-12-12
forum: Hardware
---

### Post by Sknow on 2011-12-12
This problem only occurs with Natty. I had Oneiric on here and it didn't do it but last night I switched back to Natty and it's doing it again. When I unplug the AC cord the computer goes into suspend. It's extremely annoying and I've tried a few different things but nothing seems to help. I have a Samsung N145P netbook.

---

### Post by Sknow on 2011-12-12
Don't know if it means anything or not but if I have the lid closed, unplug it, then open the lid, it comes back up like normal then immediately goes into suspend mode

---

### Post by Toz on 2011-12-12
Might be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190]("https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190"). The suggestion in the bug report is to change the way battery power is managed by running the following command in a terminal window:
```
gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false
```

---

### Post by Sknow on 2011-12-13
Seems to be working for now. I'll update when I've had a chance to try it a few more times. Thanks Toz!

---

### Post by Sknow on 2011-12-14
The problem still exists :(

---

