---
title: "SERIOUS laptop overheating and shutdown"
date: 2010-06-29
forum: Hardware
---

### Post by houbysoft.xf.cz on 2010-06-29
Hi, I have an HP pavilion dv6 1280us laptop with an AMD Turion X2 Ultra 64 bit processor and an ATI radeon graphics card.

The laptop is seriously overheating in ubuntu when the CPU is at 100% (usually when I run Handbrake, for example, but sometimes, even after a longer period of time of using it for non-CPU intensive things like browsing the web) which results in an "automatic" shutdown -- ie. the thing shuts down as if you cut power and then can't be turned on again for a while until it cools a little, I'm guessing.

It runs Ubuntu 10.04 64bit. The same thing does not happen in Windows. **It is clearly not a hardware issue.**

I've googled a lot and tried many things, like using the fglrx driver instead of the open source one which seems to have helped a little but it still overheats and shuts down sometimes.

Any pointers?

Thanks in advance.

P.S.
As a temporary solution, is it at least possible to "hard-code" the CPU frequency and disable scaling? ie. make it run at say 50% all the time?

---

### Post by nixscripter on 2010-06-29
Do you have cpufrequtils? It can save quite a bit of power by reducing your processing time.

[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)

---

### Post by RJARRRPCGP on 2010-06-29
> **houbysoft.xf.cz said:**
> Hi, I have an HP pavilion dv6 1280us laptop with an AMD Turion X2 Ultra 64 bit processor and an ATI radeon graphics card.

The laptop is seriously overheating in ubuntu when the CPU is at 100% (usually when I run Handbrake, for example, but sometimes, even after a longer period of time of using it for non-CPU intensive things like browsing the web) which results in an "automatic" shutdown -- ie. the thing shuts down as if you cut power and then can't be turned on again for a while until it cools a little, I'm guessing.

It runs Ubuntu 10.04 64bit. The same thing does not happen in Windows. **It is clearly not a hardware issue.**



Sounds like the processor fan isn't running fast enough. Does it sound like the fan is even running?

---

### Post by houbysoft.xf.cz on 2010-06-30
@nixscripter: yes, I do -- this is why it only shuts down when CPU intensive tasks are done since the CPU is scaled up.

@RJARRRPCGP: yes, it actually runs really fast (as far as I can tell from the sound) when the CPU is scaled up, but it doesn't seem to be enough (it still shuts down).

---

### Post by nixscripter on 2010-06-30
You can tell cpufrequtils to never scale up by running it on "powersave" instead of "conservative" or "ondemand". That might fix it.

---

### Post by artemyv on 2010-06-30
you may also want to check (using System Monitor or the likes) what is using CPU when comp should be idle...

I have noted on my laptop - after I used any wine program the CPU usage stays to high even after I exit it - the cause was wineserver. So I just kill 2 wine processes manually after exiting wine program - which brings CPU back to half-speed immediately

(I'm using CPU frequency scaling monitor in panel...)

---

### Post by houbysoft.xf.cz on 2010-06-30
@nixscripter: I know, but that's not really a solution.. especially in Handbrake and similar applications, it of course helps to have it at maximum.

@artemyv: that's not the problem, when it should be idle, it is, the problem is when I run CPU-intensive applications.

---

### Post by artemyv on 2010-07-01
> **houbysoft.xf.cz said:**
> @nixscripter: I know, but that's not really a solution.. especially in Handbrake and similar applications, it of course helps to have it at maximum.

@artemyv: that's not the problem, when it should be idle, it is, the problem is when I run CPU-intensive applications.

What I would suggest in this case - To try some custom solution ( I'm not able to provide it ;) just to point in the direction you could look for)

For my Acer Aspire One - I have used (maybe even am using right now ;)) - some fan-monitoring script that was scaling down the fan speed when CPU temperature was low and speeding it up when the CPU temperature was high.

You could try to find such a script and modify it to actually low CPU Frequency when the temperature of CPU is higher than High-Limit and (If CPU Scaling Monitor does it - your script probably could do it as well)

And switch back to OnDemand behavior when the temperature goes down below some Low-limit

---

### Post by guitarmaster on 2010-08-01
OK, option 1 is to open up your laptop and give it a really good once over with an air blaster, make sure you get rid of all the dust in there that will be compounding your overheating problem. Thanks to@cunningphil on twitter for this suggestion.

If that doesn't help then option 2 might be something like this, which I'm currently using and seems to be having the desired affect:

Enter the following code into a file:

```
#!/bin/bash

while :

do

if [ `acpi -t | awk '{print $4}' | awk -F "." '{print $1}'` -gt 84 ]
 then
   kill -STOP `ps ax | grep [g]hb | awk '{print$1}'`
sleep 30
   kill -CONT `ps ax | grep [g]hb | awk '{print$1}'`
fi

done

```

Save your file and make it executable. Next, start your video encoding using handbrake, and in a separate terminal window, run your batch file.

It relies on you having sensible output from the acpi command, which you ma not have by defualt. If acpi does not work for you, then try installing [lm-sensors]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29") 

You would then need to update the script to lm-sensors instead of acpi.

Let me know how you get on with this. You might need to adjust the temperature threshold. I'm using 84 degrees, which may be a little overzealous, I don't know. I'm still experimenting with it!

:D

---

### Post by guitarmaster on 2010-08-01
There is also a nice script that you can install from synaptic called "h264enc", which seems to work quite nicely. It's a little fiddly to begin with, but it is nice-able.

---

### Post by guitarmaster on 2010-08-01
OK, using the script as it is does slow things down somewhat. But I'm sure this could be improved upon by tweeking the timeout and temperature.

It may work even better in conjunction with [this]("http://ubuntuforums.org/showthread.php?t=846480")

:-)

---

### Post by guitarmaster on 2010-08-01
OK, try this one. Works much better than my previous effort, but requires you to install and configure lm-sensors.

```
#!/bin/bash

maxtemp=84
waittime=20

function action {
  echo Pausing $waittime seconds at `date`
   kill -STOP `ps ax | grep [g]hb | awk '{print$1}'`
sleep $waittime
  echo Resuming at `date`
   kill -CONT `ps ax | grep [g]hb | awk '{print$1}'`

}
while :

do

if [ `sensors | grep -i temp1 | awk -F "+" '{print $2}' | awk -F "." '{print $1}'` -gt $maxtemp ]
  then
   echo temp1 too high `date`
   action
 elif [ `sensors | grep -i Core0 | awk -F "+" '{print $2}' | awk -F "." '{print $1}'` -gt $maxtemp ]
  then
   echo Core0 too high `date`
   action
 elif [ `sensors | grep -i Core1 | awk -F "+" '{print $2}' | awk -F "." '{print $1}'` -gt $maxtemp ]
  then
   echo Core1 too high `date`
   action
fi

done

```

Variables now set at beginning of file. This really does seem to stop handbrake from shutting my machine down. Change [g]hb to [H]andbrakeCLI if the command line version is giving you grief.

Edit as required if you have more than two cores.

---

### Post by adamslade on 2011-09-11
Hi,

I am a bit of a noob and have copied and pasted the above script.

when running it I am getting the errors below:

/usr/local/bin/cpu-mon: line 18: [: -gt: unary operator expected
/usr/local/bin/cpu-mon: line 22: [: too many arguments
/usr/local/bin/cpu-mon: line 26: [: too many arguments

I would appreciate any help.

---

### Post by aimwin on 2013-01-28
I have solved problem with Hp dv6 6317tx overheating with,

1. Install Ubuntu 12.04 default out of the box got 53-65 Degree C working temp.

2. Install Ubuntu 12.10 got overheating with default installation at 65-80 Degree C, but after install AMD driver according to 
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Updated_Open_Source_Driver_PPA.27s](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Updated_Open_Source_Driver_PPA.27s)

Then got very stable 51-65 Degree C. rarely noisy fan any longer.

---

### Post by matt_symes on 2013-01-28
Old thread. Closed.

---

