---
title: "Why is gnome-system-monitor using all my CPU?"
date: 2008-10-05
forum: General Help
---

### Post by ottossonchristian on 2008-10-05
I wonder why this process uses up to 60 % av of CPU? Is lies sometimes at 10 % but together with Firefox it is the most consuming process and it is causing me some problems in general.

Is it the graphics? processor? How can I speed things up? In general the computer is slower now with Ubuntu (earlier XP) than I think it should be, although it's something like 5 years old perhaps. However I cannot say that it was better with XP because it was not then under my use.

It happens especially when I change windows or switch between programs, but also when I go from one tab to another in the very same system monitor...

And yes I have an old processor; Celeron 1.7 GHc and 512 RAM. It is using 260-350 of this Memory (60-70 %) and the Swap is below 100 MiB or 7 %. I think the RAM should be big enough...?

Any clues?

Christian

---

### Post by Kyront on 2008-10-05
The gnome-system-monitor is the process that tells you which processes are using system resources, i.e. the application "System Monitor". If your system is generally behaving sluggish, it's probably not caused by that.

---

### Post by ottossonchristian on 2008-10-07
Ok thanks for that, should I then understand it like it is normal to have a CPU-usage in that range? Or should we think that it normally should be lower (I suppose)?

Sluggish - yes, and I thought this process using all my CPU was part of the problem, as in itself I cannot understand why it should use that much. Change processor perhaps?

---

### Post by Npl on 2008-10-07
> **ottossonchristian said:**
> Ok thanks for that, should I then understand it like it is normal to have a CPU-usage in that range? Or should we think that it normally should be lower (I suppose)?

Sluggish - yes, and I thought this process using all my CPU was part of the problem, as in itself I cannot understand why it should use that much. Change processor perhaps?use top (from the commandline) for a lightweight system-monitor.

Changing Processors wont do much, gnome-system-monitor just sips alot CPU-time. Maybe theres a good reason for that... maybe its just innefficient

---

### Post by sdennie on 2008-10-07
There is a bug filed against gnome-system-monitor for this very issue (it takes huge amounts of CPU time) and I don't recommend using it.  You can use either top or htop in a terminal or you can add the system monitor applet to the panel for a lightweight persistent solution.

---

