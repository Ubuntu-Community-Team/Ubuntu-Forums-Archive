---
title: "MY laptop fan runs constantly..doesn't on windowsXP"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by linkunderscore on 2007-01-03
The thread title sorta explains it. My laptop is very quiet which is one of the things i love about it. When I installed Ubuntu however, I noticed that the fan runs constantly. It use to only ever do that when I was doing really hardcore computing without giving it much room to breath. Not only is it louder (which i don't like), it runs my battery down lots faster. Instead of 3+ hours of battery life I get ~2. 

What can I do, if anything, to fix this? 

I want Ubuntu on this laptop because its sweet, but this could be a deal breaker for me because I take it to class and I need all of the battery life I can get and the noise issue may be a problem in some of my classes. 

](*,)

---

### Post by linkunderscore on 2007-01-03
I just found this "laptop_mode" thing while messing around in command line. I did the following:

```
sudo /etc/init.d/laptop_mode start
```

I dunno if that actually does anything though.

edit: it says that its(laptop_mode) "not active, disabled"

---

### Post by 900i on 2007-01-06
I have a similar problem on my Acer, I have found that if I put the laptop into suspend mode and then resume the session the fan operates correctly and only comes back on when the cpu requires it to.  Hope this helps someone figure out what is going on as quite a few people have this problem.

Laptop-mode-tools actually spins down the hard disk between seek requests, but the hard disk has to spin up again to seek.

---

### Post by navyjeff on 2007-01-08
I've been working on a similar problem with my Dell Inspiron 1150 on every version of Ubuntu. The problem seems to be related to suspend/resume, but I'm not sure how. 

On mine, it works fine until I suspend and resume. At that point, the CPU fan runs all the time, but at levels varying based on cpu load. I was able to work around the problem by running a cpu fan control program called Dellfand, which can be found [here]("http://dellfand.dinglisch.net/"). 

Dellfand uses some rather interesting assembly code to control the hardware fan directly (as far as I can tell).  I'm wondering if there is something wrong with the ACPI driver that allows the BIOS to control the fan after a suspend/resume. Or perhaps it's the other way around.

It has been a rather vexing problem for me.  :-k

---

### Post by tweedledee on 2007-01-09
> **linkunderscore said:**
> The thread title sorta explains it. My laptop is very quiet which is one of the things i love about it. When I installed Ubuntu however, I noticed that the fan runs constantly. It use to only ever do that when I was doing really hardcore computing without giving it much room to breath. Not only is it louder (which i don't like), it runs my battery down lots faster. Instead of 3+ hours of battery life I get ~2. 

What can I do, if anything, to fix this? 

I want Ubuntu on this laptop because its sweet, but this could be a deal breaker for me because I take it to class and I need all of the battery life I can get and the noise issue may be a problem in some of my classes. 

](*,)

First, don't mess around with laptop_mode, it is an older set of scripts replaced by laptop-mode-tools (according to other threads I recently tracked down, anyway).

You can try the following:

edit /etc/default/acpi-support, and change the "enable laptop mode" line to "true" (it is probably the last line).

Then edit /etc/laptop-mode/laptop-mode.conf.  The file is well documented, you can configure a lot of power settings there.  I THINK the fan speed may be controled by the CONTROL_CPU_FREQ section, with the "ondemand" versus "performance" options.

You should also take a peek in your bios to see what it is defaulting to; you can be able to make the switch there.  (Windows managers a lot of power stuff by default that Ubuntu doesn't, I've found making a few changes the BIOS leads to the same net behavior, often even more reliably.)

---

### Post by aquamystic on 2008-02-20
since going to U7.10 my fan on the Compaq presario stays on always and freezes at sleep mode.  Been reading and trying different terminal codes,  nothing works yet.  

Discovered that my Laptop_mode is not installed, though someone said ti was an old script. . .

A HOWTO recommended using config editor to open with "CPUfreq".  I set the ac and battery policies to "powersave".

Assuming this will help my fan issue. . .  What value do I input for performance_ac and performance_battery?

If another route is best, PLEASE redirect me, been doing this for two days now!  Must get back to business.

---

### Post by brothermalcolm on 2008-02-23
@ tweedledee

I have also an Acer laptop wth a constantly running noisy fan when I boot Gutsy, and I've tried your suggestions for editing the laptop-mode config. I've allowed laptop mode tools to control the max CPU frequency by switiching option to 1, and I've set LM_AC_CPU_MAXFREQ=medium (it was fastest before). However it doesn't appear to have changed the fan speed at all cause it is still very noisy. I want to try editing BIOS settings but how can I do that?

Here's the relevant part of the laptop-mode config script I've edited:

```

#
# Should laptop mode tools control the maximum CPU frequency?
#
CONTROL_CPU_FREQUENCY=1


#
# Legal values are "slowest" for the slowest speed that your
# CPU is able to operate at, "fastest" for the fastest speed,
# "medium" for some value in the middle, or any value listed in
# /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies.
# The "governor" can be any governor installed on your system, this usually
# includes "ondemand", "conservative", and "performance". The
# "IGNORE_NICE_LOAD" setting specifies that background programs that have
# a low priority ("nice level") should not cause the CPU frequency to
# be increased. (You generally want this to be enabled in battery mode.)
#
BATT_CPU_MAXFREQ=medium
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=ondemand
BATT_CPU_IGNORE_NICE_LOAD=1
LM_AC_CPU_MAXFREQ=medium
LM_AC_CPU_MINFREQ=slowest
LM_AC_CPU_GOVERNOR=ondemand
LM_AC_CPU_IGNORE_NICE_LOAD=1
NOLM_AC_CPU_MAXFREQ=fastest
NOLM_AC_CPU_MINFREQ=slowest
NOLM_AC_CPU_GOVERNOR=performance
NOLM_AC_CPU_IGNORE_NICE_LOAD=0

```

---

### Post by cbanbury on 2008-06-04
Anyone had any luck with this issue? 
I have found loads of how to forums etc that I think have solved the problem....until my fan starts whirring like a jet engine for now reason. 

I also have a acer laptop with lm-sensors installed and by comparison of the thermal monitors lm-sensors thinks the idle temperature is 42 degrees and acpi thinks its 46...which one is right?  
Also I have no way of controlling the fans using lm-sensors as pwmconfig refuses to work. 
In fact, it is just one fan on my laptop which cools both the CPU and GPU...so I don't know which one is kicking the fan in all the time.

For me the fan noise is not constant, but comes in as bursts of around 30s of  high frequency fan noise. Has anyone else got the same issue? 
The periodic fan noise seems to be worse at temperatures around 47 degrees (acpi) and if the laptop warms up then its less frequent....which doesn't make any sense. 

Anyway, just thought I would share my findings in the hope that someone else has experienced the same or it is of some use to someone. I also use my laptop for class and the burst of high pitch fan noise are very frustrating. 
But...will...not...go...back...to W-I-N-D-O-W-S :P 

Good luck!

---

