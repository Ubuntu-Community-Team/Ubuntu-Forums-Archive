---
title: "cpu throttling down, not up"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by rmaple on 2006-02-04
Hello,
   I recently installed Breezy on a new machine, and am in the process of running prime95 to test stability, etc.  The motherboard throttles the fan based on cpu temperature, and I was curious that the fan speed has not increased, even though the processor has been running 100% for over an hour.  I did some poking around and found that powernew-k8 is running, so cool and quiet is active.  Thats fine, except that I can only find evidence that it throttled down (shortly after bootup) but never back up, based on the "grep  powernow /var/log/messages".  Also, /proc/cpuinfo shows the frequency as 1000Mhz.

How can I tell for sure what powernowd is doing, and what frequency the cpu is running, when?

My system
Athlon 64 3200+ (stock 2GHz)
Abit Kn8
1GB dual channel ram

Thanks,
Ray

---

### Post by Sutekh on 2006-02-04
You can add a Freqeuncy Scaling Applet to one of your panels, to keep an eye on the CPU speed and indeed to choose the speed it runs.

Right-click any panel and choose 'Add to Panel'
Scroll down to 'System and Hardware' and choose the 'CPU Frequency Scaling Monitor'.

Once its on the panel you need to enter the following command to allow you permission to choose the frequency.
```
sudo chmod +s /usr/bin/cpufreq-selector
```

Then you can left-click the applet, to choose the frequency or the governor (which defines the throttling behaviour)

---

### Post by joe_gosse on 2006-02-16
Thanks for the tip there. I do have a follow up question though:

What controls the CPU speed when you don't manually choose a setting? Also is there a panel item that can show system temperature?

Thanks for the help.

---

### Post by Sutekh on 2006-02-16
[QUOTE=joe_gosse]Thanks for the tip there. I do have a follow up question though:

What controls the CPU speed when you don't manually choose a setting? 
[/QUOTE]
Well this depends on the **governor**.  The governor basically controls the frequency switching behaviour.  I think by default it is on (at least on my system) **userspace**.  

You can determine the available governors by either clicking on the applet and choosing governors, or issue this command
```
cat /sys/devices/system/cpucpu0/cpufreq/scaling_available_governors
```
Here is the list of governors available
```
userspace powersave ondemand conservative performance
```
The governors are pretty self-explanatory, I mean to do some more research to find out *exactly* how they function at some point.

[QUOTE=joe_gosse]Also is there a panel item that can show system temperature?

Thanks for the help.[/QUOTE]
There is a **Hardware Sensor Applet** in the **Add to Panel** dialog.  

You should be able to get everything you need by using this, I just can't remember if anything else had to be installed.

---

### Post by alfonz on 2006-02-16
> There is a Hardware Sensor Applet in the Add to Panel dialog.

You should be able to get everything you need by using this, I just can't remember if anything else had to be installed.

you need to install sensors for that applet to work, which I haven't figured out yet. When ever I load that applet it gives me a message "no sensors detected"

Anyone has it working?

---

### Post by Sutekh on 2006-02-16
I do have it working.  Only I can't remeber how.  I think I installed lm-sensors using apt-get.
```
sudo apt-get install lm-sensors
```then run ```
sensors-detect
```

---

