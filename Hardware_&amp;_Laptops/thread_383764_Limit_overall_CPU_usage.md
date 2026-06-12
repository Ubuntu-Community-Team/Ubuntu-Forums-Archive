---
title: "Limit overall CPU usage"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by Akre on 2007-03-13
I've searched everywhere but I always get stuck by cpulimiter or some watchdogs solutions...

I have P4 laptop that is overheating, I want limit overall CPU usage to 50% or 70% for example.
I dont want to limit CPU usage per process, nor per user.

Just make sure that processor never goes above 70% limit of cpu usage.

Is the solution so obvious that I am missing it?

Thanks for help!

---

### Post by bernied on 2007-03-13
Have you checked that your fans and heatsinks are not full of dust?

---

### Post by Akre on 2007-03-14
Perhaps they are, but just for now i need solutions to resolve problem remotely, without access to computer.

And there is slight possibility that cleaning laptop will not help.

---

### Post by Nenron on 2007-03-14
I your laptop supports it (good chance it does) you can try and enable processor throttling.

Open a terminal and go:

```
cd /proc/acpi/processor
```

The list the contents of the directory

```
ls
```

You should see a directory named CPU0 or something similar (mine is C000):

So cd to that directory and list the contents of that directory, one of the files should be named 'throttling'.

if you enter:

```
cat throttling
```

you will see what your current throttling state is.

for example, I get:
```
state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%
```

The star show the current state. Note this is not the CPU level but the reverse. 0% means no throttling i.e. CPU is at 100%.

To change the state you must be root so say:

```
sudo su
```

And then you can change the state. For example to set the throttle to 50% you can do:

```

echo 4 > throttling
```

Alternatively you should also be able to so this with out a root shell by entering:

```
echo 4 | sudo tee throttling
```

 
Now read back the values:

```
cat throttling
```

And if you see something like this:
```
state count:             8
active state:            T4
states:
    T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
   *T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%

```

Then congratulations. You processor is now throttled.
At least I hope this is what you meant.

There actually might be a better solution. You can have the processor automatically throttled when it reaches a specified temperature. If you like I can try and help you out with that as well.

Good luck :)

---

### Post by Akre on 2007-03-14
Nope, It didnt help because laptop does not support ACPI. (in file it says: not supported)

But it got my attention as I've remembered that p4 support freq scalling with cpufreqd and p4-clockmod module - so it is working now - very easy to setup.

Thanks for yours replays!!

However mystery remains: my original idea was to use cpu at it original speed (2,8 Ghz) but limit it usage so it can run cooler.

---

### Post by bernied on 2007-03-14
Perhaps you only need to get the right governor going in cpufreqd. This will change speed as and when needed.
```
sudo cpufreq-info
```gets cpufreqd information
```
sudo cpufreq-set -g ondemand
```sets the ondemand governor.

If you're still worried about heat, you could write a little script that checks the temperature every minute or so, if it's too hot you can do
```
cpufreq-set -g powersave
```

Perhaps the frequency scaling is more effective at keeping the heat down than limiting CPU usage anyway?

---

### Post by Kamu on 2007-07-11
Stupid question here:  

I have a dual core so when I go to /proc/acpi/processor/ I see CPU0 and CPU1.  Can I just in turn use

cd CPU0
echo 4 > throttling
cd ../CPU1
echo 4 > throttling

?

I remember vaguely reading somewhere that throttling of all cores must be identical at all times... which wouldn't really be the case here.

---

