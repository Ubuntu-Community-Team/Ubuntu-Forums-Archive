---
title: "Can't detect sensors.."
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by MortenE on 2007-12-04
I have installed lm-sensors. 
When i run sensors i get this readout:
------------------------------------------------------
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +36°C  (high =  +100°C)                   

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +38°C  (high =  +100°C)                   
-------------------------------------------------------
I know i have more sensors (Dell XPS M1330), I'd like to control the fans, as they run constant. Why are they not detected?
If i can't solve this I'm going back to Windows. I use this laptop at school so i need it to be quiet. Battery life alså went down from almost 7 hours to 4 with Ubuntu.

---

### Post by PmDematagoda on 2007-12-04
Did you try running:-

```
sudo sensors-detect
```

After you run that and add the required modules as given, simply restart the PC, then all the sensors should work.

---

### Post by MortenE on 2007-12-04
Yes, i did. Followed i HOWTO here. 
In Vista I get fan speed, hd-temp, gpu-temp, chipset-temp, memory-temp and cpu temp.

---

### Post by MortenE on 2007-12-06
Looks like I'm going back to Windows then.. I cant take this constant fan noise..

---

### Post by tturrisi on 2007-12-06
[http://www.nervous.it/2007/11/linux-dell-xps-m1330/](http://www.nervous.it/2007/11/linux-dell-xps-m1330/)

Controlling fan speed

Install the i8kutils package and load the i8k module with:

modprobe i8k force=1

You can control the fan speed by running i8kmon and see the current temperature and fan speed by doing:

cat /proc/i8k

which will return in order:

   1. BIOS version
   2. serial number
   3. CPU temperature
   4. fan status
   5. fan rotation speed (only on some models)
   6. ac power status
   7. volume buttons status (not the multimedia buttons)

---

### Post by taehher on 2007-12-15
i tried the i8kmon method as indicated above and when i use it i can get the fans to temporarily turn off but they will pop back on within a few seconds.  

How do i change the settings so that the fans aren't on all the time?

Thanks

---

### Post by tturrisi on 2007-12-17
try:
man i8kutils
> THE I8KMON APPLET/DAEMON
========================

The i8kmon program can be used to monitor the CPU temperature and control
automatically the fans accordingly to user-defined temperature thresholds.
The program can be run as daemon or as an applet which can be embedded in
the Gnome panel (No, I don't use KDE). The program requires Tcl/Tk (>= 8.0).

The program has builtin defaults and temperature thresholds but users can
specify their own settings in configuration files /etc/i8kmon and ~/.i8kmon.
The daemon defines 4 states with different fan speeds ({0 0}, {1 0}, {1 1},
{2 2}) and for each state are defined the temperature thresholds which cause
the switching to a higher or lower state...... 

---

### Post by taehher on 2007-12-18
Thanks,

I created a /etc/i8kmon file according to the man page.

This is it:
```

# Run as daemon, override with --daemon option
set config(daemon)      1

# Automatic fan control, override with --auto option
set config(auto)        1

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
set config(0)   {{0 0}  -1  50  -1  55}
set config(1)   {{1 1}  40  60  45  65}
set config(2)   {{2 2}  50  100  55  100}
set config(3)   {{2 2}  60  128  65  128}

# end of file

```

I also added i8k to load on boot by adding it to /etc/modules along with adding the appropriate option to /etc/modprobe.d/options.

Now i get really erratic fan behavior, with the fan jumping to high and low every few seconds even though the temperature is constant at around 45 degrees Celsius with the cpu idle.


Any advice? I feel as if im getting close to nailing this problem.

---

### Post by motin on 2008-06-27
Did you come any closer to a solution? I have very high GPU temperatures and would love to see if i8kutils has proved useful for someone... :)

---

### Post by motin on 2008-06-27
> **taehher said:**
> Now i get really erratic fan behavior, with the fan jumping to high and low every few seconds even though the temperature is constant at around 45 degrees Celsius with the cpu idle.

Your config is ambiguous around the 45 degrees: Both config(1) and config(0) matches - maybe i8kmon gets confused?

However, after trying the following set-up:
```
# Run as daemon, override with --daemon option
set config(daemon)      1

# Automatic fan control, override with --auto option
set config(auto)        1

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
set config(0)   {{-1 0}  -1  55  -1  55}
set config(1)   {{-1 1}  55  70  55  70}
set config(3)   {{-1 2}  70  128  70  128}

# end of file

```

... and still experiencing the same erratic behavior, it more looks like a bug somewhere. Do we have any bug report on launchpad on this? Gotta check or report...

---

### Post by motin on 2008-06-27
Hmm, it doesn't seem to have to do with i8kmon. Running it in verbose mode indicates that it never attempts to put the fan speed at 2. 

There seems to be some other deamon running that pulls up the fan speed for some reason. When i8kmon and that other unknown process is running at the same time, the erratic behavior is easily explained. 

So, the question is what other force is driving up the fan speed... Any ideas?

---

