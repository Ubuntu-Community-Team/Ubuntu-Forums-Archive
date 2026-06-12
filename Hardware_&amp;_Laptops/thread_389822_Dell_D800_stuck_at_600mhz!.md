---
title: "Dell D800 stuck at 600mhz!"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by MikeDX on 2007-03-21
I'll try to make this as brief as possible as I have a tendency to drivel ;)

I've got a D800 laptop, supposedly running at 1.4ghz, but I cannot get the speedstepping to go above 600mhz no matter what.

Using the gnome-applet cpu freq scaling monitor, I can adjust the governor all the way up to performance but I'm not able to change the cpu from anything but 600mhz, and automatic isnt even an option!

Does anybody know if you can force it any other way? I've tried a few things and now I'm getting really frustrated as my virtual machines under vmware are running like crap as the cpu just isnt stepping up to meet the load increase!

any help would be appreciated.. Thanks in advance

mike

---

### Post by Darko-TheRaven on 2007-03-21
> **MikeDX said:**
> I'll try to make this as brief as possible as I have a tendency to drivel ;)

I've got a D800 laptop, supposedly running at 1.4ghz, but I cannot get the speedstepping to go above 600mhz no matter what.

Using the gnome-applet cpu freq scaling monitor, I can adjust the governor all the way up to performance but I'm not able to change the cpu from anything but 600mhz, and automatic isnt even an option!

Does anybody know if you can force it any other way? I've tried a few things and now I'm getting really frustrated as my virtual machines under vmware are running like crap as the cpu just isnt stepping up to meet the load increase!

any help would be appreciated.. Thanks in advance

mike

I hve this problem on my inspiron 600m, i installed some sort of cpu stepping utility called: cpufreq-selector
it allows you to set your frequency
I'll see if i can remember where i found it

---

### Post by MikeDX on 2007-03-21
I've got cpufreq-selector installed, however it doesn't do a great deal :(

```

mike@mike-laptop:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor 1400MHz
stepping        : 5
cpu MHz         : 600.000
cache size      : 1024 KB

```

that's after i've performed: 

```

mike@mike-laptop:~$ sudo cpufreq-selector -f 1400000

```


woe is me...

I do wonder, will increasing my PSU from 65W to a 90W help at all??

---

### Post by Darko-TheRaven on 2007-03-21
you must specify a -g for it to work :) took me a while to figure that out.

the -g options are:
```

performance
power-save
userspace

```

try this command:
```

cpufreq-selector -g performance -f 1400000
```

---

