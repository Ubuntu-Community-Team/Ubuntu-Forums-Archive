---
title: "New to Ubuntu; some basic questions..."
date: 2008-07-23
forum: General Help
---

### Post by Trademark Hero on 2008-07-23
Hey guys. I'm pretty much new to Linux so bear with me. I partitioned my hard drive, installation went pretty well, I partitioned 15gb at installation for Ubuntu, which should be good because it's not going to be my primary OS. This is where my first question comes from. I partitioned 15gb, and when I check it's properties, it says it has 12gb free left, which makes sense. Yet when I run Disk Usage Analyzer, it says I have 25.5gb left, which is much more than I partitioned. I have 50.5gb left free on my Windows partition, which seems about right, although I thought it had that much free before I partitioned it, I could be mistaken. My other issue is that when I went to put it into hibernation, I got some form of an error screen and had to turn my computer off. Could this be because I already had a Windows session in hibernation? Thanks in advance guys.

---

### Post by unoodles on 2008-07-23
As for the disk space issue, there appears to be a bug that makes the disk usage analyzer show twice as much space as there actually is. I can't seem to find the bug report but ill edit it in later if I find it.
As for the hibernation problem, welcome to the club. Hibernation and Suspend issues usually are because of graphics card drivers. I think the best way to solve this issue is to start a thread or bug report with you graphics card brand and driver versions (or search to find one already posted). Also you probably want to get the exact text of the error message.

Good luck!

---

### Post by Potatoj316 on 2008-07-23
You can tell disk usage analyser where to look when scanning the filesystem.  Look around in the settings for an option that lest you change those.  You probably will have 2 entries in that list, one will be / the other will be much longer than that.  You probably can delete the longer one (paste it here first for verification) to make it show the correct size.

---

### Post by Trademark Hero on 2008-07-23
Ah yeah I figured out it was doubling it. For mouse point, one just has a slash and the other says /home/mike/.gvfs. Shall I uncheck the latter?

And what part of the forum should I post that thread?

---

### Post by Archimedes0212 on 2008-07-23
to find disk usage - you can go to the terminal and type

df -h  

(the -h displays in GB and MB instead of bytes)

---

