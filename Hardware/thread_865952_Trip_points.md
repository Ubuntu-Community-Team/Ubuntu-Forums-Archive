---
title: "Trip points"
date: 2008-07-21
forum: Hardware
---

### Post by NikoC on 2008-07-21
Every time my cpu reaches about 55 °C my fan turns on (active cooling). Output of cat /proc/acpi/thermal_zone/ATF0/trip_points is as follows:
critical (S5):           100 C
passive:                 94 C: tc1=1 tc2=2 tsp=50 devices=CPU0
Now I'm using a Pentium M which easily can run at 70 °C so I tried to change the cpu trip points (read a lot of threads on how to do so here on the forum, including the powersaved work around) via e.g.:
sudo -s (or sudo -i)
echo -n "100:90:80:70" > /proc/acpi/thermal_zone/ATF0/trip_points
which always returns the following error:
bash: echo: write error: Input/output error
I thought it would have been a permissions problem, but when doing ls -l I get:
-rw-r--r-- 1 root root 0 2008-07-21 14:12 trip_points
So this should be okay...

Can somebody point me in the right direction with this one?
Thanks...

ps. running hh with kernel 2.6.24-19-generic

---

### Post by NikoC on 2008-07-21
Bumping this one ...

---

### Post by NilsE on 2008-07-21
Does the file actually exist? It does not on my system.

Try this in a terminal and manually make your entries:

```
gksudo gedit /proc/acpi/thermal_zone/ATF0/trip_points
```

---

### Post by NikoC on 2008-07-21
> **NilsE said:**
> Does the file actually exist? It does not on my system.

Try this in a terminal and manually make your entries:

```
gksudo gedit /proc/acpi/thermal_zone/ATF0/trip_points
```

You can not make manual entries in such files, I have read about 20 posts on the subject... that's why one has to work with "echo". The file exists for sure, otherwise the "cat" command would not work!

I've been doing some more reading and it seems that setting the trip points manually is no longer possible in the latest kernel(s).
Thanks for the effort though...

---

