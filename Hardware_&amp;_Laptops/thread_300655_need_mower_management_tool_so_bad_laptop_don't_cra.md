---
title: "need mower management tool so bad laptop don't crash"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by leetrefz on 2006-11-16
Hi, my crappy Toshiba satellite A70 crashes a lot due to chronic overheating. The OS it came with included a toshiba program to manage processor capacity and screen brightness. here in kubuntu there's a similar thing but it only tells me cpu frequency without lettign my adjust. I checked adept for 'pwoer management & power manager and all the things that came up for both those searches say installed, maybe someone knows a specific program or something that'll do what I need. Thanks!

---

### Post by ciscosurfer on 2006-11-16
Many Toshiba Satellite's had this problem.  They went through a few class-action lawsuits in fact.  And if you were one of the lucky ones, you received a refund of some sort.  Then they began issuing "patches" for the CPU that effectively slowed it down, thereby decreasing the likelihood of overheating.  Of course what they didn't tell people was that their "patch" took a 2 Ghz machine down to 1.2 Ghz or worse -- people became furious!  I know all about this as my girlfriend had this exact thing happen to her.  So we decided then and there never to buy from them again.  On the flip side, I hear pretty good things about Toshiba laptops as of late -- so they obviously got their act together.  As a quick aside, what basically happened was this: as laptops (and desktops) are designed, manufactured, and ultimately put together, the manufacturers most always grab their component parts from various other manufacturers.  Somewhere down the line, one of the man.'s decided to upgrade one of their parts without notifying Toshiba about the upgrade.  Needless to say, this made Toshiba mad.  And of course, this made the end-user even more furious.

I know this isn't a direct answer to your question, but I thought I'd shed some light on the overall issue for you.

---

### Post by leetrefz on 2006-11-16
ok thanks, interesting. I'm planning on getting a Via epia to replace this, but that might be months from now. This machine has had the mobo replaced with a supposedly better one. I read about folks who had theirs replaced 4 times or so. In the little toshiba power manager I always had the CPU set on low anyway or it would only last a few minutes. Must be like a crack habit on the hard disk. I hear Toshiba is moving towards the Nuclear power business, hope the problem doesn't transfer over. I firgure there must be some equivalent  little program here. I lost windows while installing kubuntu so I can't go back for details.

---

### Post by Decade on 2006-11-16
You, too, can force your Toshiba into a low clock speed.

I don't know how, but make sure a cpufreq driver for your machine and a low-power governor, possibly powersave, are loaded. I think the modules for that are p4_clockmod and cpufreq_powersave. Then:
echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

Of course, that works only until you reboot or something else changes the governor. I haven't found out all the rules for that, yet.

---

### Post by leetrefz on 2006-11-16
I searched in adept, after enabling universe (with persistent update errors) but didn't find p4_clockmod or cpufreq_powersave. "powernowd" did come up as installed however, described 'control cpu speed and voltage using 2.6 kernel interface'. it says it's less complex than cpufreqd or cpudyn. but those don't come up for me in adept either. I wonder if they don't come up because of those update errors, and whether those happen because the cpu overheats. 

Well if anyone knows how to use 'powernowd' sounds like that might work

---

### Post by leetrefz on 2006-11-17
kpowermanager sounds good too, but doesn't come up in adept at all. I'd expect to find it in system on the kmenu. I hope it's something different from the kde-guidance power manager, assuming that's the thing that only lets me adjust what to do at low battery and when lid shut. 

in system settings it says powernowd should start at boot but is not running. I tell it to start & it says 'done' but still says not running.
sudo powernowd
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 1 scalable unit:  -- 1 'CPU' per scalable unit
powernowd:   cpu0: 1600Mhz - 3067Mhz (2 steps)

the power manager in system tray (kpowermanager I guess) reports a cpu frequency of 1600Mhz, with the bar at about halfway. no way to adjust that i can find.

playing any media will make it crap out immediately, as long as i use nothing but firefox i'm ok.

---

