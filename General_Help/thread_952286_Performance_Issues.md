---
title: "Performance Issues"
date: 2008-10-19
forum: General Help
---

### Post by gloken on 2008-10-19
Hi, I've recently begun having extreme performance issues on my ubuntu box.  Processes seem to be backing up, so that I can barely even run multiple firefox windows.  I've never had issues like this under ubuntu before.   After some frustration I did an install of the latest version, but it doesn't seem to have had any affect.

Does anyone have any advice on troubleshooting this?  I'm pretty much out of ideas at this point and would appreciate any help I can get.

Ubuntu 8.10
1.9gb memory
AMD Athlon 64 x2 Dual Core 4800+

---

### Post by CharonM72 on 2008-10-19
I may be stating the obvious, but first check your resource usage in gnome-system-monitor and also check and see if any processes in particular are taking excessive amounts of processor or memory usage. And in a pinch, maybe lower appearance settings in System-Preferences-Appearance.

---

### Post by gloken on 2008-10-19
> **CharonM72 said:**
> I may be stating the obvious, but first check your resource usage in gnome-system-monitor and also check and see if any processes in particular are taking excessive amounts of processor or memory usage. And in a pinch, maybe lower appearance settings in System-Preferences-Appearance.

Yep, both processors run at fairly reasonable percentages but spike ridiculously high.  Firefox and xorg are both eating more CPU than I'm comfortable with, but that doesn't really give me any answers. 

I've got most of my desktop settings most of the way down, none of that changed prior to the problem, and it all ran smoothly before.

What puzzles me is that nothing has changed, and that I'm running linux on  an unnecessarily powerful machine with fairly little running.  It makes me wonder if I shouldn't be considering blaming hardware.

---

### Post by CharonM72 on 2008-10-19
Over time computer systems inevitably get bogged down- I've had this particular Linux system for a couple months and it's slowed considerably, but it's still quite usable. I have a 3-4 year old Windows system which has gotten almost unusably slow. Then again, I install practically everything I can get my hands on, so I'm probably a special case. In your case, though, it looks like something else. Try booting Failsafe GNOME or KDE and see if the problem persists. If not, then it's very likely a boot-time process, so check what you have running at startup (some are listed in System-Administration-Services, but apparently not all of them). Or try killing processes (that AREN'T critical) until it speeds up to find your problem.

---

### Post by Brain-free on 2008-10-19
Hi.

It has happened to me sometimes, a program that wasn't killed correctly became a CPU black-hole. It can happen and to see if this is the case do the following.

In terminal:
```
sudo apt-get install htop
```
which installs a powerful system monitor.

After it's installed type in terminal
```
htop
```
and tell us which processes eats your cpu.

PS. The reason why I'm suggesting you to install htop is because not all processes are shown in terminal.

---

### Post by gloken on 2008-10-19
Alright, thanks.  That;s definitely a lot more informative.
Firefox keeps spiking up to nearly 60% of my CPU usage, very little else is running to use CPU out of necessity - as soon as I do open something else things get far too laggy as processes back up.

I'll try a full reinstall on firefox.

---

### Post by Ryadt on 2008-10-19
Hi. Sometimes flash on firefox can really be buggy. Try installing flashblock and see if it helps reducing firefox cpu usage.

---

### Post by bodhi.zazen on 2008-10-19
> **CharonM72 said:**
> Over time computer systems inevitably get bogged down- I've had this particular Linux system for a couple months and it's slowed considerably, but it's still quite usable. I have a 3-4 year old Windows system which has gotten almost unusably slow. Then again, I install practically everything I can get my hands on, so I'm probably a special case..

In my experience Linux in general does not suffer from the degradation in performance over time that windows seems to suffer. I agree there will be some degradation, but you should not be noticing a feeling your computer is slowing down. If it is there is likely a bug => check your logs, look at your running processes (top, etc).

---

### Post by gloken on 2008-10-19
Well a full reinstall of firefox did nothing, it still eats a lot of processor.  It looks like the culprit, but I suspect that's somewhat of an illusion created by the fact that nothing else worth mentioning is running.

---

### Post by gloken on 2008-10-19
I also have a root process eating a lot of cpu.
/var/lib/gdm/:0.Xauth -nolisten tcp vt7

---

### Post by Brain-free on 2008-10-19
> **gloken said:**
> I also have a root process eating a lot of cpu.
/var/lib/gdm/:0.Xauth -nolisten tcp vt7

I... see... ati... people...

---

### Post by gloken on 2008-10-19
> **Brain-free said:**
> I... see... ati... people...

Someone give this man his prize. ;)  Yep.  I don't know what I didn't think of that myself, they've only caused every single problem I've ever had with ubuntu.

I killed my ATI drivers and I'm running like I'm supposed to again.  Which is to say, without working video drivers.  I think I'll just go buy a card that works with linux and make my life a lot better.

---

### Post by Brain-free on 2008-10-19
Out of pure curiosity, how much RAM/CPU does X eat?

Because at mine machine it eats approximately 10% RAM. Could be that your drivers are outdated. The new ones have arrived (not that they will tackle your problem, but you can cross your fingers for a placebo effect...)

---

### Post by gloken on 2008-10-19
It was something like 20-25% of my active CPU, and I don't recall the numbers for ram.  I've had enough troubles with the thing by now that I think it's time to just get a supported video card, it's onboard video on my motherboard so it isn't a real loss.

---

