---
title: "CPU temperature"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by DAC1138 on 2008-03-16
My question is regarding linux and why it seems to overheat my CPU more than windows. My laptop runs smoothly in windows, and the average idle temperature in windows is 35C. When working, max temp it gets is about 44C. In linux, idle temperature is about 41C, and when working it gets to about 54C. Why is this? I was informed that linux handles CPU workloads better than windows.

---

### Post by lswest on 2008-03-16
is this a CPU in a PC or a laptop? if it's in a laptop, i always prefer powernowd over any other CPU scaling program.  to install it:
```
sudo apt-get install powernowd
``` then the settings i usually use ```
sudo powernowd -vv -m 2
``` where -m 2=mode 2 (PASSIVE) meaning it scales slowly, and in steps, not the "aggressive" setting that's the default in Linux.  and the -vv just makes it verbose.  If it's in a PC...i'm not sure, make sure the fan (if you have one) on the CPU is running.

---

### Post by pietshah on 2008-03-16
I have the problem with my laptop (Acer Travelmate 2300) heat too much.
Currently with normal use I'm surprised that it's so warm.
Sometimes (especially when looking at a movie) it goes very warm, start smelling like burnt and starts producing weird sounds/noises.

Then I turn it off and start windows, which doesnt cause that problem.

Is it a missconfiguration of Ubuntu? (I'm using feist 7.10)
How can I solve that? I'm very afraid of burning the laptop...

Note: I've just applied the command you named here. I don't know if it would solve my problem.

thanks for your help.

Greetings
Pierre

---

### Post by pietshah on 2008-03-16
(subscribing the thread)

---

### Post by DAC1138 on 2008-03-17
It's a laptop CPU. I don't think my CPU supports powernowd, as I've already played with that. But I mean, should I really have to "play with settings?" Windows does it by default automatically. Why can't ubuntu or linux in general handle this thing?

---

### Post by Junichiromayo on 2008-03-17
Try to install powersaved.

---

### Post by DAC1138 on 2008-03-17
I have powersaved already installed.

Tried using powernowd, here's what I got:

dave@Daedalus:~$ sudo powernowd -vv -m 2
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Settings:
powernowd:   verbosity:        2
powernowd:   mode:             2     (PASSIVE)
powernowd:   step:           100 MHz (100000 kHz)
powernowd:   lowwater:        20 %
powernowd:   highwater:       80 %
powernowd:   poll interval: 1000 ms
powernowd: Found 1 scalable unit:  -- 1 'CPU' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   (for example: powernow-k7), and that it works. Check
   'dmesg' for errors.
If all of the above are true, and you still have problems,
please email the author: [email]clemej@alum.rpi.edu[/email]
dave@Daedalus:~$

---

### Post by pietshah on 2008-03-19
i have exactly the same result here...

I noticed that the laptop goes overheating only when looking at a movie.
Cunky showed me a temperature of 75° today. It looks a lot

---

### Post by DAC1138 on 2008-03-19
I'm not really asking how to fix this, but more specifically I'm asking why ubuntu and linux does this. I understand linux isn't windows, but why does linux have to be a heat demon?

---

### Post by chunchengch on 2008-03-19
I think 3D desktop effect is the major cause, it is not the problem of Ubuntu or Linux, if you have activated Compiz or Beryl, disable it and you will find evident change of the temperature of CPU.

---

### Post by chunchengch on 2008-03-19
There is no default 3D desktop effect like Compiz or Beryl in Windows, so the CPU temperature and battery life will differ much between Ubuntu Linux and Windows.

---

### Post by sdennie on 2008-03-19
> **chunchengch said:**
> I think 3D desktop effect is the major cause, it is not the problem of Ubuntu or Linux, if you have activated Compiz or Beryl, disable it and you will find evident change of the temperature of CPU.

I'm not sure that's true.  Using a properly configured composited desktop should offload a lot of processing to the GPU instead of the CPU.  

It's not really possible to diagnose a CPU heat problem without more information about the system.  What is the machine being used?  What video card does it have?  If you are using compiz, is it running with indirect rendering?  etc...

By default, Ubuntu is generally close to Windows when it comes to heat and power usage but, because of the nature of the software, with some tweaking, can be FAR superior to Windows in both aspects.

---

### Post by DAC1138 on 2008-03-21
I'm using an intel graphics card, the i810 family (855GM, for the mobile chipset)

The processor is an intel celeron P4, clocked at 2.2 Ghz.

I'm not sure if I'm using indirect rendering or not, though on the compiz website it says, "Intel GMA Cards

If you are using an Intel GMA card with AIGLX, you will need to start Compiz with LIBGL_ALWAYS_INDIRECT=1 prepended to the command line and run compiz with the --indirect-rendering option, as with the following example: 
LIBGL_ALWAYS_INDIRECT=1 INTEL_BATCH=1 compiz --replace --indirect-rendering --sm-disable ccp &"

I'm using compiz right now, but even with compiz disabled there is absolutely no difference in CPU temperature and power usage.

---

