---
title: "[SOLVED] CPU freq scaling not efficient?"
date: 2008-06-12
forum: Hardware
---

### Post by ubrox on 2008-06-12
I have been using Ubuntu for over 18 months now I think. One thing that I always notice is that the CPU scaling is not very efficient. 

let me explain:
I have the following apps open most of the time:
1) Email - Outlook / Evolution
2) Browser  - firefox/firefox at least 5 tabs
3) Im - Pidgin / Pidgin & Skype / Skype
4) Audio - Winamp / Amarok - online radio
5) laptop display + external LCD display in both windows & ubuntu
6) USB KB + Mouse

In Windows, I dont see the freq going up to 1.6 GHz unless I play games or heavy flash games.
In Ubuntu, CPU is mostly at 99% and the fan is always on. If I close off Amarok / any other media player I am using and then CPU comes down to 50% (800 Mhz). But it does keep going up even if I start typing. ike right now .. I stopped Amarok and stoppped typing this post ... its 800. The moment I start typing little fast ... goes up to 1.6 GHz. 

Is this by design? I am sure I will drain my battery fast when I am not connected to a power source. 

Thanks,
Kalyan

---

### Post by sdennie on 2008-06-12
This is by design and actually conserves the battery power.  You get most of your power savings from the C-State of the processor (basically the sleep state) and not the P-State (frequency scaling).  The power savings of deeper C-States is so high that it makes sense to quickly and frequently scale up the P-State so that it can return to the deepest sleep state as fast as possible.

---

### Post by ubrox on 2008-06-12
That does not seem right. Even on litte load the CPU is cranked up all the way to 100% and the fan is whining. I agree there might be differences in how each OS manages power saving but what gnome-panel / CPU scaling applet is doing seems less efficient than what Windows is doing. I rarely hear the fan when I am in windows while I am using the Aero interface and both the laptop LCD & the external one. But it does not take more than 5 mins for the fan to start whining once I am in Ubuntu. Its not the fan I am worried about ... obviously the power management.

---

### Post by sdennie on 2008-06-12
A few things:

1) There may be other things at work that are causing your fan to come on.  For example, some BIOSs may have a default fan policy (which linux will probably use) while some Windows driver may be controlling the fan under Windows and trying to make it quieter.

2) Remember that processors can switch states quickly and the cpufreq applet only updates periodically.  I would recommend downloading and using powertop to get a better idea of how often your CPU is actually at 100% frequency:

```

sudo apt-get install powertop
sudo powertop

```

The important number here is how long the CPU spends in C3 or C4 (if you have C4) but, you can also see how often your CPU is actually at full frequency.

3) As to why cpu scaling is more power efficient than pegging the cpu at the lowest power (on modern CPUs) first, have a look at the table close to the top of this page: [http://www.lesswatts.org/documentation/silicon-power-mgmnt/](http://www.lesswatts.org/documentation/silicon-power-mgmnt/).  

Then, think about what it means in relation to cpu frequency.  For example, on my machine, the CPU frequency can range from 800Mhz to 2.5Ghz.  If I were to peg it at 800Mhz, every time it comes out of, for example, the C3 state, it's going to take 3x as long to execute at 800Mhz than it would at 2.5Ghz however, the whole time it's doing that, it's using 4.5x more power than it would if it were in C3.  So, the faster it can execute things and get back to that lower power state, the less power it actually uses.

It seems non-intuitive, I agree but, it does actually make sense.

Hope that helps.

Edit:
This is called Race to Idle by the way.  Another example can be found here: [http://www.lesswatts.org/projects/applications-power-management/race-to-idle.php](http://www.lesswatts.org/projects/applications-power-management/race-to-idle.php)  (I would have just posted that to begin with but, couldn't find it initially).

---

