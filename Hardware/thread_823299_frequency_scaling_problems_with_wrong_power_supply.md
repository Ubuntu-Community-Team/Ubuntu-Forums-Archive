---
title: "frequency scaling problems with wrong power supply"
date: 2008-06-09
forum: Hardware
---

### Post by philipppixel on 2008-06-09
Hi everyone,

this one took forever and a brand new bootstrap installation to solve [which was def. not neccessary]:

[short version] consider a better power supply when you run into frequency scaling problems [/short version]

I have a Dell Latitude D820 notebook with Intel Core 2 Duo running Hardy Heron with KDE 3.5.9, the processor is capable of 2 x 1.83 GHz. fine so far. Usually one thinks the processor uses the maximum speed - even with power attached. Not so in my case :( It just wouldn't run with full 1.83 GHz, instead with 1GHz.

Originally the Kubunt came from a Dell Inspiron with different hardware setup and I thought I must be an errornous Installtion due to the hardware shifting. But I do lots of software engineering so I really need the CPU power for compile stuff and test environment.

I googled every forum with Ubuntu and frequency scaling problems and even one suggested that he has no scaling problems without power supply attached. Well this worked for me, but no solution in sight.

After a brand new Installation things went okay in the first place. But back at work the same problem occured! *crazy. CRAZY!*

I found out that I have two different power supplies: one with 90W and one with 65W. I am used to attach latter one at my work place. When replaced by a better power supply it sure RAN at 1.83 GHz.

I didn' expect this behaviour while the notebook gets power by the power supply.

I hope this helps anybody in the future.
So long and thanks for the <')+++<

PPxL

---

### Post by ja4 on 2008-10-22
I'm having the same problem with 8.10 (Ibex) on a Dell Latitude E6400 with Intel Core 2 Duo T9400 @ 2.53GHz.

If I plug in a 90W adapter then frequency scaling works;
 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq 
2535000


Plug in a 65W adapter and frequency is frozen at the minimum 800 MHz; 

 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq 
800000

 Unplug the AC adapter and run on battery power and frequency scaling works again.  

 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq 
2535000


So I am free to run at max speed or use the Performance setting when on battery alone, but not on battery+65W adapter.  Arrgh.


Is this a problem with cpufreqd or powernow, or the BIOS?

---

### Post by ja4 on 2008-10-28
I found out that the Dell BIOS limits the frequency to 800 MHz when the 65W travel adapter is used.  Apparently this is to prevent underpowering of the discrete (not integrated) graphics card.  

Dell neglected to inform buyers that this would happen if they purchased only the 65W adapter.  

Boo Dell.

---

