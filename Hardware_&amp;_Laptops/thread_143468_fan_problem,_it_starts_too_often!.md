---
title: "fan problem, it starts too often!"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by IGNIZ on 2006-03-12
hi, i've an hp pavilion ze4355ea and my fan really starts too often, powernowd and cpufreq are running, my cpu clock is set to 500 mhz, but fans starts the same really often and the wind is coming out is cold! so there is no need for fan to start. before ubuntu i had slackware and fans weren't starting so often, any idea? 

sorry if my english is not so good :rolleyes:

---

### Post by IGNIZ on 2006-03-12
maybe it's because  /proc/acpi/thermal_zone/THRM/cooling_mode is set to "active" and it should be  passive? how can i set it to passive?

using sensor applet i've only one sensor, and the fan starts at 51° and stops near 40°, i think it starts for nothing or it's a good temperature for the fan to start?

---

### Post by IGNIZ on 2006-03-13
up

---

### Post by Felix21685 on 2006-03-13
im just a newb but..

whats wrong with the fan starting too soon.
i have 2 in my case and i leave them running all the time...
you can't have enough airflow in a pc case in my opinion..

---

### Post by IGNIZ on 2006-03-13
this is not the normal behaviour of my laptop, and if it can be less noisy i really would want to do it:
with xp fan started something like every 20 minutes for 1 minute
with slackware every 30-40 minutes for 1 minute
ubuntu is something like always on! and temperature never goes over 55°

---

### Post by ibanez88 on 2006-04-22
Igniz I'm experiencing the same problem.  I think the fan always being on is adversely affecting my battery life compared to WindowsXP.  Your last post was some time ago, did any of the possibilities above help?

---

### Post by ozorba on 2006-04-22
This may be an acpi problem. I did not have this problem until I installed Dapper Beta.

The CPU speed keeps on ramping up to maximum and staying there for a long time without any reason. I thought that it would stay at 800Mhz most of the time.

And here is the CPU Info:

$ cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      no
limit interface:         no

Can anyone solve this?

---

### Post by molinex on 2006-04-22
Try installing powernowd 0.97. Dapper drake beta has 0.96. It worked for me today :)

---

### Post by IGNIZ on 2006-04-23
just installed 0.97, in slack i had 0.97, maybe was this the problem, i will update this thread after a bit of testing

---

### Post by ozorba on 2006-04-24
powernowd with Dapper behaves as it should. It operates in default mode. The clock immediately  jumps  to the  highest  frequency  whenever CPU usage goes over 80%, and decreases by "step" Hz as usage drops below 20%.  

I have used 'top' command and noticed that gnome-cups-icon process pushess the CPU load to above 80% most of the time when the pc is idle.

Is there a way of changing the priority of this process?

---

### Post by souki on 2006-04-30
[quote=ozorba]powernowd with Dapper behaves as it should. It operates in default mode. The clock immediately  jumps  to the  highest  frequency  whenever CPU usage goes over 80%, and decreases by "step" Hz as usage drops below 20%.  

I have used 'top' command and noticed that gnome-cups-icon process pushess the CPU load to above 80% most of the time when the pc is idle.

Is there a way of changing the priority of this process?[/quote] 

the default mode is 1 (AGRESSIVE)
you can try with mode 2 (PASSIVE) which is the opposite behaviour
see 'man powernowd' for details about modes

create or edit the /etc/default/powernowd
```
OPTIONS="-q -m 2"
``` 
restart the powernowd service
```
/etc/init.d/powernowd restart
``` 
you can check that it worked with
```
ps ax|grep powernowd
```

---

### Post by jchau on 2006-05-02
look into "nice" that will allow you to change the priority of the process.  You can also use system monitor to do so (Applications -> System Tools -> System Monitor): right click on the process and select change priority.

nice will change the process of something you have not run yet. eg.
```
nice -n 15 john -restore
``` where "-n 15" tells it to run the process at a lower priority, "john" is the actual command, and "-restore" is the option for john.

You can renice something (change nice level after it starts running) by typing
```
pidof john
```, where "john" is the command, to find the pid of the program.

Then run renice:
```
sudo renice 9 -p 1234
```, where "9" is the new nice level (raise priority), and "1234" is the pid of the command you want to change.  "sudo" is needed since only root can raise the priority or lower the nice level.


For more info, consult:
```
man nice
man pidof
man renice
```

---

### Post by jchau on 2006-05-02
Oh, and powernowd will not count nice'd processes when calculating processor usage. I'm not sure though if that means both increase & decreased priority or just decreased priority.

---

### Post by souki on 2006-05-02
[quote=jchau]Oh, and powernowd will not count nice'd processes when calculating processor usage. I'm not sure though if that means both increase & decreased priority or just decreased priority.[/quote] powernowd with mode PASSIVE will try to keep frequency the lowest as possible, so, decreased priority

from my eperience, I use PASSIVE mode on my laptop and it is a very silent mode : the fan stays off and I don't feel my laptop less responsive. I shut down powernowd to launch vmware when I need full cpu.

from the powernowd man :
```
MODES
       There are 4 modes supported by this client:

       Mode  0,  SINE,  changes the frequency as a sine wave function, raising
       the frequency by "step" Hz every time the CPU usage goes over 80%,  and
       decreases it by "step" Hz when the CPU usage falls under 20%.

       Mode 1, AGGRESSIVE, changes frequency by a sawtooth function.     Imme&#8208;
       diately jumps to the highest frequency whenever  CPU  usage  goes  over
       80%,  and decreases by "step" Hz as usage drops below 20%.  This is the
       default behavior.

[B]       Mode 2, PASSIVE, is the inverse of  AGGRESSIVE.   Immediately  jump  to
       lowest  frequency when usage drops below 20%.  Raise by "step" Hz if it
       goes above 80%.[/B]

       Mode 3, LEAPS, immediately jumps to the highest frequency if  usage  is
       above  80%,  and  immediately jumps to the lowest frequency if usage is
       below 20%.
```

---

### Post by jchau on 2006-05-02
[QUOTE=souki]powernowd with mode PASSIVE will try to keep frequency the lowest as possible, so, decreased priority[/QUOTE]

Wait, exactly how does the passive mode decrease the priority of processes?

---

### Post by souki on 2006-05-03
[quote=jchau]Wait, exactly how does the passive mode decrease the priority of processes?[/quote]
sorry, this has nothing to do with, I've misunderstood
I mean : priority to decrease the cpu frequency

---

### Post by ozorba on 2006-05-05
Actually the problem with the fan is caused by gnome-cups-icon. If I can turn this one off while I am not printing anything it would be wonderful. Then my cpu frequency will stay low all the time.

When powernowd Mode 1 is used with Xubuntu the fan does not turn and the speed stay low while the laptop is idle. This is because gnome-cups-icon is not running.

I really like Mode 1 of powernowd and trying to figure out to turn gnome-cups-icon off when not needed.

---

---

