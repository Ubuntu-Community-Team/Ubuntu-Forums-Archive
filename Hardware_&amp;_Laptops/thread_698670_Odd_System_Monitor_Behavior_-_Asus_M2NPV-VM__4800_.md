---
title: "Odd System Monitor Behavior - Asus M2NPV-VM / 4800 Athlon64 x2"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by phineaus on 2008-02-16
I recently parted out my old PC and brought a new case, motherboard, processor and HD.  Until last week, I was running the regular version of Gutsy, and was experiencing odd behavior and crashes after the computer had been on for a while.  Then, I realized that I maybe should be using the 64 bit version, and switched to that.  Still experiencing the same issues.  

CPU:  Athlon64 x2 4800 2.5 GHz
MB:    Asus M2NPV-VM
HD:  WD 320 Gb SATA

I am not sure what info people are going to recommend that I include in this thread, but just let me know and I will post my results.  

Basically, I can see both processors in system monitor, And they each have a separate color line on the CPU history graph.  Everything seems reasonable, and I can multitask however I desire when the computer is up and running.   However, after between 5 and 12 hours, I start to experience serious sluggishness that soon renders the computer useless.  During these periods I notice that the system monitor will show a solid 50% CPU usage.  Then, as it gets worse, I see either a 50% or 100% SHADED usage on the monitor.  I have not seen this before, and not sure what it means.  Its just usage show behind the regular blue, in a lighter blue.  

After reinstalling with AMD64 Gustsy (preserving /home on its own partition), I am thinking it must be a configuration problem specific to this hardware.  Interestingly, if I catch it fast enough, I can just restart Xwindows, log in again, and its fine!  

Any leads?

---

### Post by Krydahl on 2008-02-16
I'm using the same board and haven't seen anything similar - but I suppose yours could be dodgy somehow.

Have you tried identifying what process is using all the CPU when it does this?

---

### Post by phineaus on 2008-02-16
I have checked the processes, and nothing seems out of the ordinary.  That the confusing part.  The sys monitor shows the shaded CPU usage, but then if you open it, the actual CPU usage is only shown based on the usage shown by the regular solid blue...

---

### Post by Krydahl on 2008-02-16
Huh. No idea what shaded CPU usage means, Not seen that.

Try typing top into a terminal next time it happens. That shows you a list of what processes are running and updates it regularly to put the ones using most CPU at the top of the list.

---

### Post by phineaus on 2008-02-17
That command is useful, but just presents the same information as the system monitor does in graphical form.  In any case, like I mentioned above, there is no process that is using the CPU.  Sometimes its 0% usage, but the computer bugs out.  Today it happened again, and I restarted Xwindows.  Upon that simple restart, I had no more issues.  Has anyone had any problems with X configuration and my motherboard and/or processor?

---

