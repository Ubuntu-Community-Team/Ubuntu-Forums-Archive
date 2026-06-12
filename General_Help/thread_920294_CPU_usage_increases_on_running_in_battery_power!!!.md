---
title: "CPU usage increases on running in battery power!!!"
date: 2008-09-15
forum: General Help
---

### Post by dayanandasaraswati on 2008-09-15
Hello friends, Today i noticed a peculiar problem. i'm using Dell Inspiron 1525 Laptop,  Intel Centrino Dual Processor, 2GB Ram. I'm running firefox and totem now. My cpu load says 30% in both of my processors. I was running on AC power when my cpu showed 30%. Now when i unplug the ac power, and run on battery power, my system monitor shows both cpu usage as 60%. I did the same thing for almost ten times and am finding the same thing. This is the most peculiar problem which one can encounter. Please find me a solution for this as increased cpu load in battery mode means more battery power consumption which is not good.

---

### Post by prshah on 2008-09-15
> **dayanandasaraswati said:**
> 
I was running on AC power when my cpu showed 30%. Now when i unplug the ac power, and run on battery power, my system monitor shows both cpu usage as 60%. 

First of all, which CPU monitor are you using? The one in system-resource has bugs.

Second, when you unplug AC, your processor may be stepped into a lower speed (In my case, CeleronM steps down to 600Mhz from 900 Mhz), and as a consequence, percentage CPU usage should go up; ie., even though there is no actual step up, since it is now measuring percentage power on a lower maximum, the percentage should go up.

Third, your CPU usage may initially shoot up when you remove AC power, but should again settle down within a few minutes; maybe you should wait about 3-5 minutes before checking CPU usage.

---

### Post by dayanandasaraswati on 2008-09-15
Oh is tat really so..Facinating..How can i measure to what speed my processor is stepped down to. How do i really measure it. I use the default gnome system monitor. Also top command in the terminal shows similar bugs. I watched for prolonged time. It reduces a bit but doesnt settle to the 30% mark. Anyway how do you find what speed is your cpu currently running at..?

---

### Post by sdennie on 2008-09-15
Try using a combination of "top", "cpufreq-info" and "powertop".  If you notice that on battery, the machine switches to "powersave" or that powertop is showing the CPU constantly at the lowest frequency, you may want to switch the CPU governor to ondemand (which should be the default):

```

sudo cpufreq-selector -g ondemand

```

Having said that, if you are using your machine on battery and constantly have it at 60% (or even 30%) CPU, I think your power savings are going to be pretty limited.  You could verify what kind of effect this has on power savings using the powertop tool I mention above.

---

### Post by prshah on 2008-09-16
> **dayanandasaraswati said:**
> 
how do you find what speed is your cpu currently running at..?

Right click an empty area in your panel; choose "Add to Panel"; Add the "CPU Frequency Scaling Monitor" applet. This will display the speed and stepping in realtime for your CPU(s).

---

