---
title: "CPU frequency at 1.2Ghz for a 2.0 Core 2 Duo CPU."
date: 2008-08-29
forum: Hardware
---

### Post by amn108 on 2008-08-29
Hello all,

I am running Ubuntu 8.04.1 LTS and everything seems to be in top shape. I am wondering however, my frequency monitor applet in Gnome shows always 1.20Ghz for both cores. I patched the cpu_governor setting in gconf-editor to get maximum performance, but why won't the CPU scale up to it's marketed frequency? 

Since I am running 'performance' governator, i thought it's no holdback maximum speed? Don't see much point in buying a 2.0Ghz CPU otherwise.

My thought is that at 2.0Ghz the CPU should stay idle more, since it finishes its business quicker. No?

Anyways, how to scale it up to 2.0Ghz?

---

### Post by nicedude on 2008-08-29
It will only run at 2.0GHZ when it is needed to, like if you play a 3D game etc. My systems all run at lower speeds when not busy, but go fast as possible if pushed to need to do so. While the main advantage of this is power savings it also is probably easier on the CPU this way and also should keep the CPU's temps low, both of which would help it have a long service life. So unless you are experiencing CPU related slowdowns then this is the way it is supposed to be. 

Hope this helps

---

### Post by tamoneya on 2008-08-29
its called intel speed step and it is enabled in the bios.  Try disabling it and then it will continuously run at full speed.  Assuming this is a laptop (we are in the laptop sub forum) you should know though that running at 2.0 GHz consumes more power than 1.2 GHz and therefore a decrease in battery life.  Personally I run my 2.0 GHz dual core (T7300) at 800 MHz normally and it steps itself up whenever I need it.

---

### Post by amn108 on 2008-08-31
Thanks guys. I think it only switches to 2.0Ghz after prolonged periods of intense CPU activity. I have never seen it reach 2.0Ghz yet, and I do my usual desktop thing. I run on AC. And yes, I know very well what SpeedStep is, but I guess nobody to blame for you not knowing this but myself, since I neglected to mention it...

I guess it is not that important...

---

### Post by sdennie on 2008-08-31
It's surprising that on performance it wouldn't go up to 2.0Ghz because the performance governor should force it to max speed at all times.  You could try seeing if you can force it to 2.0Ghz with cpufreq-selector:

```

sudo cpufreq-selector -f 2000000

```

Some other things to try:

```

sudo cpufreq-selector -g userspace
sudo cpufreq-selector -g ondemand

```

There used to be a bug where the frequency would get stuck unless I switched to/from userspace.

---

### Post by amn108 on 2008-09-05
I did what you suggested. 'sudo cpufreq-selector -f 2000000' puts the governor to be 'userspace' and the frequency jumps up to 1.2Ghz (not more). What I found out is that any value you supply as frequency number to the cpufreq-selector command gets approximated to either 800Mhz or 1.2Ghz, I do not ever see any other frequencies for the CPU I have.

Seems strange...

---

### Post by amn108 on 2008-09-05
```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: userspace, conservative, ondemand, powersave, performance
  current policy: frequency should be within 800 MHz and 1.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 800 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 2.00 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: userspace, conservative, ondemand, powersave, performance
  current policy: frequency should be within 800 MHz and 1.20 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).

```

The above is the trace of the 'cpufreq-info' command. The weird (and bizarrely obvious) thing is that if you take a look at the 'available frequency steps' section, it lists 2Ghz twice. Also for some strange (and unquoted) reason it says that the 'current policy' is that frequency should be within 800Mhz and 1.20Ghz. It is a mystery, why and who has decided this range, when the section above lists 1.60 and 2.0Ghz as steps too. I am being kept in the dark :-)

I am going to go into the BIOS, and switch some CPU controls there, and see if it resolves this limit.

---

### Post by amn108 on 2008-09-05
No effect from BIOS control tweaking.

I have now searched the net for the occurencies of the same issue, and I do find people with similiar problems. None of them has been solved.

The problem appears to lie inside the 'cpufreq' kernel module, or some ACPI software internals. Possibly depends on BIOS DSDT tables. In any case, it seems to be a rather complicated issue.

Mind you, the problem has nothing to do with CPU frequency control software like 'powernowd', 'cpufreqd' or 'cpudyn'. These are merely userspace tools to manage CPU frequency, but they all talk to either the sysfs interface or cpufreq kernel module. The latter appears to be called 'acpi_cpufreq'.

A very good indication of the problem is 'cat'ting the '/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq' file. Even though my frequency ceiling is 2.0Ghz, no matter what I do, i get '1200000' from the file. Also, the 'scaling_available_frequencies' file in the same directory outputs '2001000 2000000 1600000 1200000 800000' which, considering the abnormal '2001000' frequency value, is a bit weird (may be completely normal though).

So far the problem remains.

---

### Post by amn108 on 2008-09-23
The problem has to do either with Ubuntu unable to interface ACPI properly when a battery is absent and laptop is on AC, or the firmware/hardware itself has a bug which causes the CPU to lock to 1.2Ghz upper limit when the battery is removed and the laptop is on AC.

When a battery is put back in and laptop is on AC or battery, the CPU may scale to 2.0Ghz.

This is the weirder bug among the ones I ve been into, and I do not see any reason it should not be fixed. It is a shame it is unfixed. What does a removed battery have to do with CPU clock?

---

### Post by juamez. on 2009-03-26
I have this problem only when I'm apparently stressing my processor. I have a Pentium M 1.87GHz, which runs at a temperature of approximatly 70°C when fully stressed at maximum clock. Ubuntu doesn't seem to like this in a mysterious way and decides to lower the maximum allowed clock to lower some steps before the temperatures dives beneath a certain threshold, I guess somewhere around 50°C, at which it will then rise again untill the maximum clock is reached again, given that the temperature doesn't get high again.

This is the output as it started lowering my cpu frequency.
```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 1.87 GHz
  available frequency steps: 1.87 GHz, 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, powersave, userspace, performance
  current policy: frequency should be within 800 MHz and 1.33 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.33 GHz.

```

Right now I have stopped stressing the processor, and the frequency is slowly rising again:
```
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 1.87 GHz
  available frequency steps: 1.87 GHz, 1.60 GHz, 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, powersave, userspace, performance
  current policy: frequency should be within 800 MHz and 1.60 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.60 GHz.

```

What in god's name is that anyway? And how can I change or disable it? It annoys me.

---

### Post by amn108 on 2009-03-26
Figures, you appear to be using a 'userspace' governor. In other words there is an application installed at your setup which controls the cpu speed, as opposed to the more usual 'ondemand' governor which is a stock kernel based governor. That application may have its own weird logic, f.e. capping the ceiling frequency when things get too hot.

You either installed that userspace governor yourself or someone else did it for you, or your distribution uses it as default.

The default 'ondemand' governor that Ubuntu uses does NOT cap ceiling frequency, I would know because I am using it in my Thinkpad with a Pentium M 2.0Ghz Banias CPU.

In any case, it is useful to add the CPU Frequency Monitoring applet to a Gnome panel of your choice. Use the 'Add to panel..." panel context menu choice and find that applet, add it and it will not only show what frequency your CPU currently switches to, but also if you click on the applet it lets you change the governor and lock the CPU speed manually, for instance to 1.87Ghz.

A governor is a program that decides and controls how to clock the CPU. Obviously different programs follow different logic.

But maybe you know all this already?

If you want to dig more, you can see what is contained in files in /sys/devices/system/cpu. Lots of info can be gathered from there, and in fact thats the interface everyone else uses in their software, as it is exported by the kernel and its modules.

---

### Post by juamez. on 2009-03-26
My systems used the ondemand governor as default, but I changed it from performance to userspace while fiddling around with the settings. Ondemand is a nice governor, but if you are into wine gaming, you'll find that it sometimes makes the performance of the game choppy and stuttering, while that isn't so when setting the cpu to the maximum frequency regardless of its stresslevel.

This maximum frequency "fallback" I first noticed when I changed from ondemand to performance. After a while of gaming at the maximum frequency and thus a high temperature, I noticed the clock going down slowly at the predefined steps. I then suspected the performance governor for interfering with the clockspeed, so I used userspace governor (to no avail, unfortunately) by putting this line in my /etc/rc.local file:
echo userspace > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor && cpufreq-selector -f 1870000 || exit 1

I should add I noticed the drop in clockspeed because I already had the cpufreq applet on my taskbar, along with a system monitor applet to monitor the cpu-load, so nothing new there.

I know there are a lot of files listed in the directory you mention, but I never got around to checking every file while suffering from forced clockdown. I'll get back to it later when I think about it a the right moment.

Thanks for trying to help me out anyway!

---

