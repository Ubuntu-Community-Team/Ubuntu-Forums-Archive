---
title: "CPU always at 800 mhz on battery (Hardy)"
date: 2008-08-23
forum: Hardware
---

### Post by goeagles520 on 2008-08-23
Hello there,

I am new to ubuntu and really like it, except for one major problem. 

I have a Dell m1330 (with a T9300) and when I am plugged into AC, my CPU scales as it should (I can see it go between 800 mhz and 2.5 Ghz in the panel when I run super pi). However, if I unplug the laptop from AC and run it on battery, the CPU seems to get locked into 800 mhz. When I run super pi, it stays at 800 mhz as well.

If I then replug in the laptop to AC, the scaling works as it should

Are there any thoughts on how I can resolve this?

Thanks,
GoEagles

---

### Post by bubba_169 on 2008-08-23
Press alt+f2 and run 'gconf-editor'

Navigate the tree to apps -> gnome-power-manager -> cpufreq

If policy_battery shows 'powersave' next to it, click on this and change it to 'ondemand'. That should work :)

---

### Post by goeagles520 on 2008-08-23
Hi bubba,

I actually don't have cpufreqd. This is a vanilla install of ubuntu. When I navigated gedit to the place you said, the cpufreqd file wasn't there...

-GoEagles

---

### Post by sdennie on 2008-08-23
What bubba_169 recommended should be correct.  Also, for that laptop, you may want to have a look at this thread which can increase battery life by 50% in some cases: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773").  In that script, you can manually force the CPU to use ondemand if you so choose.

---

### Post by bubba_169 on 2008-08-23
> **goeagles520 said:**
> 
I actually don't have cpufreqd. This is a vanilla install of ubuntu. When I navigated gedit to the place you said, the cpufreqd file wasn't there...


You should be using GCONF-EDITOR not GEDIT. I am using a vanilla install of ubuntu too and the option is there :D

---

### Post by goeagles520 on 2008-08-23
Woohoo...keeping my fingers corssed but it seems to have worked!!

Thanks bubba and vor!

---

### Post by goeagles520 on 2008-08-23
quick question...

in gconf-editor for cpurfreq, it says that performance_ac is at 85. Why is that? Can I set it to 100 without any damage to my system?

---

### Post by bubba_169 on 2008-08-23
I think the performance_ac field chooses when to scale up to cpu, not what value to scale to. At 85 it means when the cpu reaches 85% usage it will scale up the speed to the next step available...

EDIT: actually now I think about it I'm not so sure if thats true?

---

### Post by goeagles520 on 2008-08-23
Yeah, I don't think thats right either. By default, the performance_battery value was set to 25. If I left it like that, I didn't get scaling on battery. When I changed it to 85, it did scale...

---

