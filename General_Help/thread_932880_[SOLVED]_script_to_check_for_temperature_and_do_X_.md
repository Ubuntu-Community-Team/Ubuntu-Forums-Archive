---
title: "[SOLVED] script to check for temperature and do X in case of..."
date: 2008-09-28
forum: General Help
---

### Post by itxaka on 2008-09-28
Hello!

I know, I know, the title is horrible but I couldn't think of anything better :)

Let's explain.

I go a nice laptop running Ubuntu 8.04.
I got sensor and sensord installed.
I got an apache server running with php5-ffmpeg
I am running a small youtube-like site in it for a few friends (less than 10)
ffmpeg does the conversion process when a video/audio file is uploaded
My CPU is a Amd 1,8Ghz with 3 steps, 800Mhz, 1600Mhz and 1800Mhz
Normally I run it at 1800Mhz


Now to the problem, normally the laptop runs 24/7 so this friends can upload their videos to share between us. The laptop normally maintains a nice temperature.
BUT sometimes, when uploading large videos, ffmpeg takes a while to convert them and the CPU temperature goes really high and makes my laptop turn off automatically.
As always, this happens in the middle of the night, thus preventing anyone to check his videos or upload anything. Sometimes it happens when I am travelling and they have no access for a week.

When running the laptop at 800Mhz it doesn't matter if I'm encoding 100 videos, it runs smoothly (but slow) and the temp never goes too high.

Now to the main question.

I know that sensor gives the temperature + sensord send it to syslog
I know that I can set the speed of the cpu with cpufreq-selector -f 800000

**Now I need someone to give me some directions into creating a script (preferably that runs in the back) that checks every minute for the temperature value and if it's X it launches the cpufreq-selector to 0,8Ghz in order to cool down the computer and when the temperature is X-30 it launches it again to put it at 1,8Ghz.**

This way, in case of someone uploading a large video or simultaneus uploads and encoding going on the computer will not shutdown itself, it will encode slower but it will be up and running

Is this possible (and easy!)?
Any suggestions?

Thanks to all!

---

### Post by olejorgen on 2008-09-29
That should be simple. Template:
```

#!/bin/sh

INTERVAL=$((1*60)) # in seconds
CRITICAL=70
SAFE=60

while true; do
   sleep $INTERVAL
   TEMP=$(<command to get temp>)
   if [ $TEMP -gt $CRITICAL ]; then
       cpufreq-selector -f 800000
   elif [ $TEMP -lt $SAFE ]; then
       cpufreq-selector -f 1800000
   fi
done

```

For my laptop this command gets the temp:
```

awk '{ print $2 }' /proc/acpi/thermal_zone/THRM/temperature

```

Run the script from /etc/rc.local like ```
myscript **&**
```

---

### Post by itxaka on 2008-09-29
wow. Awesome!

Thanks man!

Just a question, I can unerstand the script really well but there are two thing that I can't. What does "-gt" and "-lt" do exactly?

Also, what should I change in order to see exactly what the script is doing? Like seeing the output of the command to get the temp and seeing when cpufreq is invoiced?

I want to do that in order to closely monitor the script for a few hours in order to optimize the critical temp and safe temp.

Thanks!

---

### Post by kpkeerthi on 2008-09-29
-gt = Greater than
-lt = Any guesses?

Put some echo statements in the scripts and redirect the output to a log file so you can see whats going on within the script.

---

### Post by kpkeerthi on 2008-09-29
```

#!/bin/sh

INTERVAL=$((1*60)) # in seconds
CRITICAL=70
SAFE=60

while true; do
   sleep $INTERVAL
   TEMP=$(<command to get temp>)
   [COLOR="Red"]echo "Current time is `date`"[/COLOR]
   [COLOR="Red"]echo "Current temperature is $TEMP degrees"[/COLOR]
   if [ $TEMP -gt $CRITICAL ]; then
       [COLOR="Red"]echo "Switching to low-power mode"[/COLOR]
       cpufreq-selector -f 800000
   elif [ $TEMP -lt $SAFE ]; then
       [COLOR="Red"]echo "Switching to turbo mode"[/COLOR]
       cpufreq-selector -f 1800000
   fi
done

```

And start the script as below:
```

myscript > /var/log/mylog.log 2>&1

```
* Make sure you have permissions to write to /var/log/

---

### Post by itxaka on 2008-09-29
> **kpkeerthi said:**
> -gt = Greater than
-lt = Any guesses?

Put some echo statements in the scripts and redirect the output to a log file so you can see whats going on within the script.



d'oh! ;)

Thanks a lot, It's actually running great after a few tries to blown it up :)

---

### Post by forger on 2008-09-29
-lt is lower than, as *man sh* reveals :)

Here's a tip on how to search huge manuals:
type: man sh
then press: /-lt
and press Enter
(press q to exit)
It will search for the text string "-lt"

---

