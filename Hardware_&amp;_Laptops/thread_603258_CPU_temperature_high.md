---
title: "CPU temperature high?"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by pillu on 2007-11-04
Hi all,

I am running Gutsy 7.10 on Lenovo 3000 laptop (1.66 GHz Core 2 Duo, 1 GB RAM). The fan runs a lot more under Ubuntu than under Windows XP. This could either be because windows has crappy thermal management and doesn't switch the fans on or that the processor heats up a lot more under Ubuntu. I am currently using the Gnome sensors panel applet to monitor my CPU temperature (never managed to get lm-sensors working correctly). Here is how the temperature and the fans behave

1. On startup the temperature is around 43 C. Fans are quiet.
2. After a few minutes of browsing, viewing files etc the temperature jumps up to 51C and fans switch on
3. Temperature creeps up to 53 C. The fans are buzzing away in all their glory now. This seems to be the steady state temperature because it never cools below this and hence the fans never stop running.

What i would like to know is

1. Are these temperatures too high for normal operation?
2. Is it ok to change the fan setpoints so that they switch off when the temp settles at 53 C? If so, how do I do this?

Any help in solving this situation will be much appreciated.

---

### Post by ozPATT on 2007-11-05
I have had a few issues where my computer has shut down due to reaching critical temperature - 100degrees. 

This has happened about 6 times in the last 4 weeks. So today I bought a laptop riser, and now with it sitting on that I have the following: 

>  Thermal 1: ok, 54.0 degrees C
     Thermal 2: ok, 57.0 degrees C


They also seem high to me. Is this normal for a laptop?  Sorry I dont know the answers to your problems pillu, just figured I must be havingthe same problem..

Thanks

Patrick

actually I did just notice something interesting... my laptop has been working all afternoon around 57 degrees. I just left it for about 20mins, while I watered the garden. I came back and it was on 80! I hadnt been doing anything! Except the screensaver was on... I have no started typing this, and in the time taken to type this addition, it has dropped from 80 to 69 and is still going down, i suspect to the 57 it was on before... 

does anyone know what is happening there? Is the fan not working when the screensaver is on, or is the screensaver sucking up so much juice that the fan cant cope?

---

### Post by pillu on 2007-11-05
100 degrees is definitely too high....Even 80 degrees is probably too much. Have you tried opening up your laptop and cleaning the vents with compressed air. The thermal grease between the processor and the heat sink might also have crapped out....

Does Windows also show the same behaviour? 

My problem is that the laptop heats more in Ubuntu than under WinXP. This indicates that this is more of a software issue. Any ideas anyone?

---

### Post by newagelink on 2007-11-05
OP: I have the opposite issue (although it's not a problem for me.) In Windows, my fan is frequently running, even when I'm not doing anything.

In Ubuntu, my fan is rarely on, and only kicks on when I'm heavy multitasking. Same level of heat both ways ... 

We're both using Ubuntu 7.10, but I've a Gateway laptop. Maybe the problem lies in hardware?

Edit: I was confused. I'm using 7.04.

---

### Post by dimbulb1024 on 2007-11-05
I run a Intel Pentium M and it's operating range per Intel is -40C to +85C. Maybe find out the exact chip you have and check Intels specs.

---

### Post by jemarroyo@gmail.com on 2007-11-09
Hi I'll present my case its very similar:
I dont know the motivs but my Kubuntu Gutsy seems to overheat my Laptop.
It doesnt overheat in other OS. So hardware is OK.
When I boot in Gutsy the temperature is around 42 ºC but in ten minutes the temperature get to 60 and then the fan starts and never stops. Finally the temp is around 56. If I have lot of work to do the laptop easily turn over 70 ºC.
I don't know whats wrong.
I deactivate: Strigi and there is not hanging proceses.

Arroyo Jorge

---

### Post by jespdj on 2007-11-09
You could try using powertop to see if there are any processes that stress the CPU. Install it with:
```
sudo apt-get install powertop
```
Then open a terminal and run it with:
```
sudo powertop
```

My laptop doesn't have this problem. When idle, the CPU temperature is 40-45 C, and if I let it work it heats up to maybe 55 C, I haven't seen it getting much hotter than that. I have a Core 2 Duo T7300 (2.0 GHz).

---

### Post by jemarroyo@gmail.com on 2007-11-09
Thanks I have already test **powertop** and nothing seems to repair the overheat.
I'm following this forum and I think that it will solve my problem.
[http://www.ubuntu-forum.com/showthread.php?t=539365](http://www.ubuntu-forum.com/showthread.php?t=539365)
For the first time the CPU does not turn over 50 ºC. I'm testing the solution.
Then I will tell you
Thanks a lot
Arroyo Jorge

---

### Post by ozPATT on 2008-01-05
Hi all, I still am having issues with my laptop overheating, more so now that the hot weather has kicked in here. I am using the laptop riser still, but I am still running at anywhere between 65 and 75 degrees, ocassionally hitting the 80 and above. 

I have installed powertop as suggested above, but I am not sure it makes much sense to me... this is the output from it:

>   PowerTOP version 1.8       (C) 2007 Intel Corporation

                                      P-states (frequencies)
                                        1.60 Ghz     0.0%
                                         800 Mhz   100.0%


< Detailed C-state information is only available on Mobile CPUs (laptops) >

Wakeups-from-idle per second : 312.1    interval: 10.0s
no ACPI power usage estimate available

Top causes for wakeups:
  25.8% (161.3)       <interrupt> : eth0, nvidia 
  25.3% (158.1)       <interrupt> : extra timer interrupt 
   7.5% ( 46.9)       <interrupt> : HDA Intel 
   6.5% ( 40.6)               esd : schedule_timeout (process_timeout) 
   6.5% ( 40.6)               esd : do_nanosleep (hrtimer_wakeup) 
   5.4% ( 33.6)       <interrupt> : ohci_hcd:usb1 



i have compiz installed, and have the wobbly windows and the desktop cube on it, but i dont understand the above very well.. what is a wakeup and I am guessing that it isnt a good thing? I have a compaq presario v3000 series with AMD Turion 64 x2 processor and nvidia graphics card.

Any advice would be good

Thanks

Patrick

ps, after writing this yesterday, I was clearing out my recycle bin that had about 10Gb in it, so it took a while to clear.. during that time my temperature soared, even touching 99 degrees at one point, and staying around 95 degrees until it had finished deleting everything. how can I check that my fan is working properly? is there a way to manually turn it on/off?

---

### Post by pillu on 2008-03-23
the solution at
[http://www.ubuntu-forum.com/showthread.php?t=539365](http://www.ubuntu-forum.com/showthread.php?t=539365)
seems to work for me. The cpu temperature hasn't gone above 50 degrees since I implemented the second part of the solution. I also cleaned my vents, which might be the reason for the cooler cpu as well.

~pillu

---

