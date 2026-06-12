---
title: "Ubuntu 9.10 install changed my clock?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by XP_convert on 2009-10-31
I have a strange situation - I ran Ubuntu 9.10 live cd on a PC with Windows XP Professional installed, and then installed it onto the hard drive. I selected the proper location / timezone during install for my region.
 
The first strange thing I notice is that Ubuntu changed my PC clock to 7 hours back, both in Ubuntu, and in Windows XP. Minor annoyance but Jaunty never did that.
 
I'm working on problem #2 - my wireless does not work in 9.10, so I'll have some fun troubleshooting that... :popcorn:
 
 
Anyone else here had Ubuntu 9.10 change the system time / clock?

---

### Post by dvlchd3 on 2009-10-31
I could be wrong, but I believe the Ubuntu installer attempts to set the system clock to UTC time.  Then, Windows/Ubuntu should subtract/add the appropriate hours from the system clock to match your time zone so you have the correct time displayed in your OS.  I have no idea what the purpose or usefulness of this is, but I believe I remember seeing something along those lines.

If you change your clock in WinXP and Karmic, the change should stay consistent after a reboot.

---

### Post by slugicide on 2009-11-03
I'm having a similar problem. Every time I log in to Windows 7 or Ubuntu 9.10 the clock is wrong and I have to manually correct it. I'm totally baffled as to what to do.

---

### Post by mcooke1 on 2009-11-03
After I installed 9.10 my wireless was gone I fixed it by using Synaptic Package Manager and removed Network Manager and at the same time installed WICD then rebooted and its fine now. You can go to System, administration, time and date and fix the clock issue.

---

### Post by slugicide on 2009-11-03
Thanks, but that only allows me to adjust the clock. It will still be wrong the next time I log in to Windows or Ubuntu.

---

### Post by mcooke1 on 2009-11-04
Every time I install Ubuntu I have this clock issue  even though I select the correct zone for where I live. You can try changing it in your computers set up, reboot press F2 (this may be different on your computer) at the same time and change it there. Or with windows right click on the clock and reset the internet time. Or with Ubuntu download the package required to synchronise with internet time. These methods have worked for me.

---

### Post by amopresunto on 2009-11-09
The problem is the UTC.  There is a [solution]("http://ubuntuforums.org/showthread.php?t=1143877").  For convenience, here is the solution.....


[QUOTE=SentientFluid]By default Windows uses local time so when you adjust the time it sets your BIOS time to match.  Ubuntu (and all other *nix distros I know of, including OS X) use UTC time.

Last I checked you could tell Ubuntu not to use UTC time by using the following steps:

In Terminal...
```
sudo cp /etc/default/rcS /etc/default/rcS_backup
sudo gedit /etc/default/rcS
```The first command backs up the file, the second opens it for editing.

Change...
```
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=yes
```
to...
```
# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no
```

I haven't tested that in a long time, though.[/QUOTE]

---

### Post by garvinrick4 on 2009-11-09
You are changing in BIOS?  I had same but fixed.

---

### Post by SlappyFrog on 2009-12-20
On the recommendation of a friend, I tried the LiveCD.  I made the LiveCD tonight using the latest download.  I tried it by selecting the Try Ubuntu with out changing anything option and after awhile I rebooted my system.

Upon launching Windows XP, my system clock was set wrong, like the users in this forum.

The LiveCD promised not to touch anything and it apparently did and I find that to be incredibly aggravating.

---

### Post by jemaze on 2009-12-20
> **SlappyFrog said:**
> On the recommendation of a friend, I tried the LiveCD.  I made the LiveCD tonight using the latest download.  I tried it by selecting the Try Ubuntu with out changing anything option and after awhile I rebooted my system.

Upon launching Windows XP, my system clock was set wrong, like the users in this forum.

The LiveCD promised not to touch anything and it apparently did and I find that to be incredibly aggravating.

I was the recommender and was able to reproduce this issue on a separate machine, yikes!

---

