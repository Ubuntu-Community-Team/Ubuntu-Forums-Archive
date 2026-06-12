---
title: "Laptop constantly overheats since ugrading to Hardy"
date: 2008-07-16
forum: Hardware
---

### Post by chrisrx on 2008-07-16
Since upgrading to Hardy my laptop fans have been running extremely loud and the bottom of the laptop too hot to sit on my lap.

I know that before Hoary, my processor would normally only use 1GHz and that switch up to 1.83GHz when it was needed,  but now I find that the laptop is always running at 1.83GHz and I don't know how to stop it.

The laptop is a toshiba satellite pro a120 with a core 2 duo processor.

Thanks in advance

---

### Post by pauper on 2008-07-18
Well, before jumping to conclusions have you performed anything from paragraph 
"1)" (see below) between Hoary and Heron?

To avoid overheating stick to the following:

1) Develop a casual cleaning maintenance routine (!!! use proper guides or ask
   for a qualified help):

 * blow compressed air through laptop vents;

 * disassemble your laptop (check the link from my signature) once in a while
   (might void warranty), clean the air pathways and the fans
 ([http://www.mhc.ab.ca/services/educational-technology/resources/cleaning.htm](http://www.mhc.ab.ca/services/educational-technology/resources/cleaning.htm));

 * reapply thermal grease ([http://www.hardwaresecrets.com/article/274](http://www.hardwaresecrets.com/article/274));

2) ALWAYS use the laptop on a HARD SURFACE, elevate the back of the laptop to
   get more decent level of air circulation;

3) DO NOT operate your system in extreme ambient temperatures (below +41°F or
   above +95°F);

4) Consider purchasing a cooling stand for a laptop;

5) Don't run multiple memory hungry processes at the same time: heavy gaming
   or graphics applications, compiling programs, ripping DVDs, running virus
   scan, etc.;

6) Consider setting your CPU frequency to lower rate (see "man cpufreq-selector",
   [http://www.mjmwired.net/kernel/Documentation/cpu-freq](http://www.mjmwired.net/kernel/Documentation/cpu-freq)); which should bring
   down the heat generation and power consumption.

---

### Post by PHATSPEED7x on 2008-07-18
I have a sony laptop, and since I starting using ubuntu on it it runs way cooler. For some reason windows XP really made it hot. Running a cooling pad helps alot too.

---

### Post by StormPCs on 2008-07-18
How is the CPU utilization at idle?  It should be close to zero unless you're running Compiz and other such desktop enhancements, in which case it should still be well under 15%.  If it's higher than that you could have software and/or driver issues.

---

### Post by XCIX on 2008-07-25
My Toshiba satellite does that too, and I am running on Xubuntu (which should require less memory).
The freak-of-nature funny issue is that it seemed cooler on Windows Vista... it makes no sense.
suspect some memory configs might need to be twitched

pauper, thank you. Will try some of your advice.

---

### Post by phidia on 2008-07-25
You may want to have a look at [Powertop]("http://www.lesswatts.org/projects/powertop/") & [this]("http://packages.ubuntu.com/hardy/powertop") too.

---

### Post by chrisrx on 2008-07-27
I haven't performed any maintenance to the inside of the laptop because I am pretty sure it is only a problem with Ubuntu.  When I'm running XP I don't get this problem.

My Idle use is normally about 10-15% because I'm running compiz, but the only thing that makes it go high over that is flash, which makes my fans go into overdrive instantly.

---

### Post by am7146 on 2008-07-27
I have an old HP/Compaq NC4010 and my power use was:

[LIST]
[*]Fawn: Low.  Ran for hours. Way better than XP.
[*]Gibbon: Sucked power like an aluminum smeleter.  Ran 1/2 as long on battery as Fawn.  used PowerTop to research it, but no avail.  Something (but not listed) was waking it thousands of times per second.
[*]Heron: Much better than Fawn, but not great.  17 watts, as reported by powertop.  Usually C2, 600mhz.  229 wakeups-from-idle per second.  And to get the power use down I had to do a clean reinstall.  When I did an upgrade, power was just as bad as with Gibbon.  Before that, it was so hot I could pour batter on the keyboard and make waffles.
[/LIST]

do:
```
sudo apt-get install powertop
```

and run 
```
sudo powertop
```

and see how many wakeups from idle and your watts.  Read [http://www.lesswatts.org/](http://www.lesswatts.org/) for more info--there's a ton of stuff on saving power in Linux there.  If you get obsessive, though, you can become like one of those hypermilers that focuses on squeezing the last watt out of your system and spend all day futzing with settings and such...

Good luck! 

Andy-

---

