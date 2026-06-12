---
title: "Frequency scaling on 2nd core?"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by dave_abrahams on 2006-08-09
My Core Duo Thinkpad (T60p) my CPU frequency scaling monitor shows that even when there's essentially no load, CPU0 is getting scaled back to 46%, but CPU1 runs at 100% continuously.  I'm running the latest i686 (SMP) Dapper kernel.

Does anyone know how I can enable frequency scaling on the 2nd core?

Thanks,
Dave

---

### Post by 5-HT on 2006-08-10
Are you running powenowd or one of the kernel governors?
Dapper's powernowd (0.97) should have SMP support and there shouldn't be a need to configure anything (just make sure you're using the userspace governor).

---

### Post by dave_abrahams on 2006-08-10
> Are you running powenowd or one of the kernel governors?

I don't know; where can I learn about the difference?  I can find lots of offhand references to these things on the web, but no comprehensive guide.

As of last night I followed [http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06_Flight_6_on_a_ThinkPad_X60s#CPU_frequency_scaling](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.06_Flight_6_on_a_ThinkPad_X60s#CPU_frequency_scaling)
and now I am getting frequency scaling all right.

> Dapper's powernowd (0.97) should have SMP support and there
> shouldn't be a need to configure anything (just make sure you're
> using the userspace governor).

Well, sysfs.conf was all comments before I followed the above-mentioned instructions; I could try switching the setting on both CPUs to "userspace" and see what happens, but I'd really like to understand what I'm doing.

  man sysfs.conf

and

  man sysfs

don't yield anything but a "No manual entry" message.

...but now I'm wondering if powernowd is really what I'm after.  Having seen its documentation it looks like it *only* does frequency throttling, and even with the 2nd CPU throttled back, my battery life is only a little over 3 hours for nonintensive tasks (e.g. text editing) when I could get nearly 5 hours on Windows XP (I really want ubuntu to be my primary OS!).  The fan speed is still 3300 RPM, which makes more noise than I'd like.  

I'm not sure that powernowd's simplicity is as much of a virtue as its docs imply.  It's probably more likely to work OOTB with a wide variety of systems, but I really would like to have the kind of controls I can get under XP that allow me to set things up for maximum performance or maximum battery life, control the temperature, etc., depending on the system's power state.

When I search for "CPU frequency" in Synaptic I find at least three other alternatives (cpudyn cpufreqd kpowersave).  How does one choose among these?

---

### Post by dave_abrahams on 2006-08-10
> **dave_abrahams said:**
> I could try switching the setting on both CPUs to "userspace" and see what happens, but I'd really like to understand what I'm doing.

For the record, changing "ondemand" to "userspace" leaves me with both cores running at 100% speed under no load.

---

### Post by 5-HT on 2006-08-11
[quote=dave_abrahams]For the record, changing "ondemand" to "userspace" leaves me with both cores running at 100% speed under no load.[/quote]

If the ondemand governor is working great with both cores it may save you some headaches to stick with ondemand over the userspace governor and powernowd. As  you oberserve no throttling when using the userspace governor, perhaps powernowd is not running?
You can check with ```
 ps aux | grep -i powernow 
``` 

[quote=dave_abrahams]
...but now I'm wondering if powernowd is really what I'm after.  Having seen its documentation it looks like it *only* does frequency throttling, and even with the 2nd CPU throttled back, my battery life is only a little over 3 hours for nonintensive tasks (e.g. text editing) when I could get nearly 5 hours on Windows XP (I really want ubuntu to be my primary OS!).  The fan speed is still 3300 RPM, which makes more noise than I'd like.  [/quote]

AFAIK, Linux isn't quite up to Windows in regards to battery life-- though it's hopefully only a matter of time.

You could try enabling laptop-mode if it isn't already. Laptop-mode will help to conserve battery life by delaying writes to the hard disk and increasing disk cache. Please refer to the following thread: [http://ubuntuforums.org/showthread.php?t=218926](http://ubuntuforums.org/showthread.php?t=218926)

About having more control over power-management (such as fan control), there may be some specific applications for Thinkpads (not really sure as I don't have one myself). You may find what you're looking for by searching ThinkWiki or these forums.
Sorry I couldn't be of more help.

---

