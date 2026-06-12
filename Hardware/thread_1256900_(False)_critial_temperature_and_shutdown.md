---
title: "(False) critial temperature and shutdown"
date: 2009-09-03
forum: Hardware
---

### Post by paolo.pani on 2009-09-03
Hi,

I have Ubuntu Jaunty on Dell Studio XPS 1330.
After I have upgraded to Jaunty, once in a while the system (apperently randomly) turns off.
During the shutting down, I get a message like:

"Critical temperature reached (144 C)..shutting down"

The temperature is always 144 C, but it is fake. I monitor the CPUs temp and (at most) it is 78-80 C.   

I saw that other users had the same problem...I did not undestand whether they solved it or the didn't... any suggestions?

Thanks

---

### Post by automaton26 on 2009-09-03
80 C is still too high - you should check that all the fans inside the case are still working.

---

### Post by paolo.pani on 2009-09-03
> **automaton26 said:**
> 80 C is still too high - you should check that all the fans inside the case are still working.

Thanks for the reply. 80 C is the max temp I have monitored (extensively using both CPUs). During normal usage the temperature is in a range 60-70.. it is pretty hot, but I think that the problem is due to a wrong reading of the real temperature (which is not 144!)

---

### Post by automaton26 on 2009-09-03
What are you using to monitor it?

Can you see if there are any processes that are constantly using 100% CPU? This might cause overheating at random times.

---

### Post by paolo.pani on 2009-09-03
> **automaton26 said:**
> What are you using to monitor it?

Can you see if there are any processes that are constantly using 100% CPU? This might cause overheating at random times.

I use the gnome-panel applet "CPU frequency scaling Monitor" (I guess it just reads cputemp) and I log the temperature each second. From the log file,  the temperature is always constant, much much below than 144 (says around 70) and it is not increasing right before the shutdown.

No, there is no 100% CPU usage process. The problem occurs (apparently) randomly, even without any hard process

---

### Post by paolo.pani on 2009-09-03
I add that the problem is pretty much the same as

[http://ubuntuforums.org/showthread.php?t=1139339&highlight=Critical+temperature](http://ubuntuforums.org/showthread.php?t=1139339&highlight=Critical+temperature)

but I have a different laptop

---

### Post by sergiom99 on 2009-09-03
You can monitor temperature with lm-sensors:
1) ```
$ sudo apt-get install lm-sensors
```

2) ```
$ sudo sensors-detect
```

3) ```
$ sensors

[I]acpitz-virtual-0
Adapter: Virtual device
temp1:       +30.0°C  (crit = +95.0°C)

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +27.0°C
Core0 Temp:  +24.0°C
Core1 Temp:  +33.0°C
Core1 Temp:  +31.0°C
[/I]
```

And I would start by compiling my own DSDT file. Its easy and it helped a lot in mine: 
[http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

---

### Post by paolo.pani on 2009-09-04
Thanks,
yes sorry, that's what I had installed.
If I run sensors I get

acpitz-virtual-0
Adapter: Virtual device
temp1:       +66.0 C  (crit = +105.0 C)  

I have a dual core, shouldn't I see 2 CPUs then?

Thanks

---

### Post by paolo.pani on 2009-09-06
Hello again,

the problem just happened again, this time 1 minute after the login, with no particular process running and at about 60 C...

Did any of the users which experienced the same problem actually solve it?

---

### Post by szdavid on 2009-10-31
Hi,

I have exactly the same issue with my laptop : that is really annoying !

In order to be able to work for a long time, I have to use Windows because in that case it does not crash...

---

### Post by jrusso2 on 2009-10-31
As someone suggested if its a desktop I would check the fans and make sure they are running.

If they are then maybe its dust or the heatsink is not seated properly.

The thermal temperature shutdown is often in the bios settings so I think it must be getting hot even if the number reported is wrong.  Check in the bios and see when it supposed to shutdown.

---

### Post by paolo.pani on 2009-10-31
> **szdavid said:**
> Hi,

I have exactly the same issue with my laptop : that is really annoying !

In order to be able to work for a long time, I have to use Windows because in that case it does not crash...


Hi, I solved it switching to KDE.. I know that's no a proper solution of the problem..but I was thinking about switching to KDE for a while and this just gave me a good reason :)

But this also means that there was something wrong with the gnome power manager, I guess..

---

