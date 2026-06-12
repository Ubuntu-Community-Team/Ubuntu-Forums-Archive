---
title: "Stupidly Hot AMD64 CPU on HP Pavillion"
date: 2010-10-13
forum: Hardware
---

### Post by hgernhardt on 2010-10-13
Folks—

I've been searching the net far and wide, and I just can't seem to find a solution to this problem.  I'm running Kubuntu 10.04 LTS 64-bit on an HP Pavilion dv5-1002nr, have compiled and installed k10temp, and generally have a healthy system which tells me how hot it is.  The CPU is an AMD Turion X2.

The problem I face is that there appears to be neither documentation nor hack in order that I might have the CPU fan run based upon temperature as well as load.  Currently, I'm looking at a CPU load of around 20% and a CPU temp of around 75C, yet the fan is still at the low end of its speed domain.

I've looked in /proc/acpi/fan to no avail (the directory is empty).
The fan ignores the "Always On" BIOS setting.

Is there anything that anyone knows of that will help this situation?  I'll take any pointers I can get (preferably valid, and preferably of type char*), and I'm also willing to dig into low-level stuffs if necessary.

Thanks ever so much,

Henry

---

### Post by mescobal on 2010-12-15
Same here (HP-DM3 1023). Couldn't find any hint. If you solved the problem please post it.

---

### Post by hgernhardt on 2010-12-16
Although I'm still listening for any information that may be forthcoming, I've unfortunately found no software solution.  The only things I can think of is a physical solution.  Right now I make sure I have airflow by the thermal exhaust port, which assists in keeping the temperature below heat stroke.  Other than that, the only thing I think I'm going to be able to do is to replace the cooling unit.  The one in the laptop is farily well crudded up.

---

### Post by Auax on 2011-06-04
Well, this topic is quite old, so I'm hoping someone's found a solution by now. I'm running 11.04 on a dv5-1119nr, and fancontrol still finds no fan. The fan constantly runs at a very low speed, even when I'm peaking close to 80c on core temps. The always-on bios setting changes nothing.

---

### Post by beholder88 on 2013-04-25
Bump on this. I've got a Pavilion dv5 2077cl, with the exact same issue. The fan seems to run at a constant slow speed instead of changing with the CPU load like it did when I was using Windows 7. I too have searched for days now to no avail, and am getting worried I may have to go back to Win 7 to restore any usability to my laptop.

---

### Post by overdrank on 2013-04-25
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

