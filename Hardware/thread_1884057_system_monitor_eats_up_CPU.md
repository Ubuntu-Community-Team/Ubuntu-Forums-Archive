---
title: "system monitor eats up CPU"
date: 2011-11-20
forum: Hardware
---

### Post by awesan on 2011-11-20
If I launch system monitor on my dual core (4 with hyper-threaded) core-i5 HP laptop (with integrated Intel graphics card) connected to external monitor "System Monitor" on Ubuntu 11.10, CPU usages of the following processes go high:
dbus-daemon 80-95%
gnome-system-monitor 20-5%

I cannot close the gnome-system-monitor window. I had to kill "gnome-system-monitor" from a shell. 
Work-around : Use htop and don't launch "System Monitor".

---

### Post by Jagoly on 2011-11-21
Same here. But I've got a slightly faster i7 so I can still manage to close it. Didn't happen in 11.04. Pretty useless: OK lets see what is using up all our CPU cycles: It's the monitoring application! Oh wait...

---

### Post by Sonsum on 2011-11-21
> **awesan said:**
> If I launch system monitor on my dual core (4 with hyper-threaded) core-i5 HP laptop (with integrated Intel graphics card) connected to external monitor "System Monitor" on Ubuntu 11.10, CPU usages of the following processes go high:
dbus-daemon 80-95%
gnome-system-monitor 20-5%

I cannot close the gnome-system-monitor window. I had to kill "gnome-system-monitor" from a shell. 
Work-around : Use htop and don't launch "System Monitor".

I have an HP G62 with an i5 as well, and while system-monitor does say it's using a lot of resources, running another monitor concurrently reveals that rarely any CPU is being used. I've had the problem in Rainmeter in Windows where it counts 100% as a single processor core so I've had usages of 250% or so from some hardcore programs. Perhaps it's a similar issue.

---

### Post by nixomose on 2012-01-27
same problem here. running gnome system monitor makes dbus eat up lots of cpu.

I've heard lots of bad things about dbus, but never fear, it will be replaced soon enough by something that sucks even more.

But it might fix the gnome system monitor problem.

I installed xubuntu so perhaps it's the loading of whatever gnome crap is required to make the sysmon work is causing the problem.
Who knows. Oh well.

any suggestions to a graphical alternative?

htop is nice, but I like the history gsysmon provided.

---

