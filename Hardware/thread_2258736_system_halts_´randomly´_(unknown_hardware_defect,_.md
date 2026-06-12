---
title: "system halts ´randomly´ (unknown hardware defect, where to check?)"
date: 2014-12-30
forum: Hardware
---

### Post by w@si on 2014-12-30
My notebook (Dell Inspiron n7010) abruptly halts down after some 10 to 60 mins of use. It mostly happens when system load is slightly raised (surfing with a dozen tabs open, maybe one running some flash content), but I couldn´t observe a common denominator to all crashes. Often, the machine runs a little hot and the systems slows down heavily one or two minutes prior to the abrupt halt.

The machine suffered from some weird hardware issues since it was new (4 years ago). Notably, at bootup stage, it sometimes complained I woud use an incompatible charger (while it´s the original one). Lately, the above described behaviour happend more and more frequently under the formerly installed MS Windows 7 system. Few times, the notebook´s battery led showed blinked in red a fterwards (but the crashes also happen with no battery inserted). But generally the system and all it´s components work fine. I then formatted the disk and intsalled Ubuntu 14.04 a few days ago. The hw support for the machine is quite fine (only screen brightness change doesn´t work, and seemingly there should be some driver issues with the Broadcom wifi card) but the described problem persists.

How can I find out which component might be causing the problems? How can I find a system log telling me what might have happened prior to the halts?

Thanks already.

---

### Post by TheFu on 2014-12-30
This happens to me when I've run out of RAM and virtual memory (i.e. swap).  On netbooks, RAM is generally at a premium and the default swapfile size is too small.

Since I've made the swap file 4G, my Chromebook with only 2G of RAM hasn't crashed. 2G for swap just isn't enough for a desktop anymore.

---

### Post by tgalati4 on 2014-12-30
Boot without the battery.  See if the behavior changes.  If it improves, get a new battery.  

Welcome to the forums.

---

### Post by tokyobadger on 2014-12-30
[quote="w@si"]It mostly happens when system load is slightly raised (surfing with a dozen tabs open, maybe one running some flash content)[/quote]
[quote="w@si"]Often, the machine runs a little hot and the systems slows down heavily one or two minutes prior to the abrupt halt.[/quote]
Sounds like flash at first look.

1. Next time you boot up, before you start your browser, open system monitor and note the memory and swap usage. 
2. Then start the browser and do what you usually do.
3. In system monitor click the processes tab and then click on the memory column (5th from left) - this will sort the processes in ascending order of memory usage.
4. Note how much memory your browser and "plugin-container" are using.

I've recently noticed extreme memory consumption by plugin-container (over 10G of memory - I usually have 30+ tabs open but this was not an issue in the past).

No idea if this is your issue but it wouldn't hurt to rule it out. You can disable flash in your browser to reign in the memory usage. If that doesn't help, then it must be something else - maybe a cooling issue due to dust build-up?

---

