---
title: "Laptop Overheating in Karmic"
date: 2009-12-12
forum: Hardware
---

### Post by thegladaitor on 2009-12-12
I think it started to happen ever since I installed the updates in Karmic including the new kernel ( now going back to kernel never really helps )
You can see the output here : 
nishant@ubuntu:/proc/acpi/thermal_zone/THRM$ cat *
<setting not supported>
<polling disabled>
state:                   ok
temperature:             85 C
critical (S5):           98 C
passive:                 90 C: tc1=2 tc2=3 tsp=50 devices=CPU0 
It always hover around 85 and if I really start any apps it shuts down . 
Windows is a lot cooler ( no puns intended ) . 
Can anyone tell me whats the root cause ? 

Rgds
Nishant

---

### Post by peterroots on 2009-12-12
I have a rather similar problem
```

cat /proc/acpi/thermal_zone/THRM/*
<setting not supported>
polling frequency:       2 seconds
state:                   ok
temperature:             55 C
critical (S5):           101 C
passive:                 101 C: tc1=9 tc2=2 tsp=1800 devices=CPU0
active[0]:               101 C: devices= FAN
active[1]:               101 C: devices= FAN

```
I have my fan running continuously on high to maintain this temperature by using toshset -fan high but even so acpi thinks the fan is off. (as I have a toshiba latptop)
```

cat /proc/acpi/fan/FAN/state
status:                  off

```
It seems to me that the default trip points are set to a silly value - if I understand the output correctly acpi will allow the processor to reach a critical temperature of 101c before it bothers to turn on the fan. I don't know what it plans to do to the processor with tc1=9 and tc2=2 but I hope tsp=1800 does not mean it will try to change the processor speed to 1800MHz as the speed range for my processor is only 600 - 1500
acpitool does think my fan is on though, which is something I suppose

It looks like thegladiator has stupid trip points set as well - not a friendly thing for Karmic to do IMHO

---

### Post by thegladaitor on 2009-12-12
Thanks for that .

My typical output for top is like this . Infact FF might go to 15-20% at times . I just went for a break of 10-30 mts and still showing 83 . Very high for an OS I think , Windows doesnt heat like this .
Tasks: 160 total,   2 running, 158 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.6%us,  2.7%sy,  0.0%ni, 91.2%id,  0.2%wa,  1.3%hi,  0.0%si,  0.0%st
Mem:    500120k total,   466296k used,    33824k free,    36240k buffers
Swap:   538092k total,   120936k used,   417156k free,   192132k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 2242 nishant   20   0  381m 100m  21m S  3.8 20.7  19:22.33 firefox                                                                                         
 1003 root      20   0 59752  16m 6992 R  1.7  3.3   3:54.36 Xorg                                                                                            
 2672 nishant   20   0 59104 9940 6156 S  0.4  2.0   0:05.04 gnome-terminal                                                                                  
  800 messageb  20   0  3880 1448  716 S  0.2  0.3   0:01.54 dbus-daemon                                                                                     
 1473 postgres  20   0 45320  440  368 S  0.2  0.1   0:00.87 postgres                                                                                        
 1508 root      20   0 22616  828  692 S  0.2  0.2   0:20.73 cpufreqd                                                                                        
 1809 nishant   20   0 95992 7896 4260 S  0.2  1.6   0:53.24 compiz.real                                                                                     
 2642 nishant   20   0 69356  15m 7292 S  0.2  3.1   0:30.90 xchat                                                                                           
 4676 nishant   20   0  187m  40m  16m S  0.2  8.4   1:47.99 totem                                                                                           
 5617 nishant   20   0  2468 1184  884 R  0.2  0.2   0:00.07 top

---

### Post by peterroots on 2009-12-12
I have just tried installing powersaved (as mentioned in some other posts such as [http://ubuntuforums.org/showthread.php?t=846480&highlight=trip+points](http://ubuntuforums.org/showthread.php?t=846480&highlight=trip+points))
I added some more trip points to the file /etc/powersaved/thermal and rebooted.

The fan comes on at around 66 or more (as it used to - now don't ask me what is bringing it on at low speed at that temp, I have no idea) and then off again.
The trip points in my thermal zone are as they were according to a cat of THERM and powersave -T shows the same set of trip points i.e the ones I entered in the powersave config file are not being taken into account.
If I switch the fan on with toshset both a cat of FAN/state and powersave -F show the fan to be off.

So, no progress and two problems as far as I can see
One - the trip points found in THERM are not sensible
Two - something else apart from acpi is involved in controlling the fan

On top of this powersaved does not seem to do what it is supposed to do.

---

### Post by thegladaitor on 2009-12-12
Installing power saved itself made a huge difference and my temp is around 70C now .I will try the steps u mentioned and play around with trip point and see how better we can make it .

But it seems that the frequency of the laptop has gone down to 1.33 GHZ from 1.87 GHZ .
Is that a tradeoff involved ? Is there way any we can make the CPU at its best and then deal with this heating issue ?

Thanks
Nishant

---

