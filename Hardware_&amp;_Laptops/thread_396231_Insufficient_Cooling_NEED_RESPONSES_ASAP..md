---
title: "Insufficient Cooling: NEED RESPONSES ASAP."
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by DigitalXeron on 2007-03-29
Hello, I'll cut to the chase:

My laptop (Acer Travelmate 2310 - SiS chipset) is having problems with sufficient cooling, I've tried EVERY howto on these forums, however, every one of them leads me to a report about a kernel module that isn't installed, or not loaded, I load the ones that are installed and they don't cause errors, I don't see any problems, no output, they seem to load without error, However, there obviously is a problem.

LM sensors says it can't find anything:
#########
 Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 [http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html](http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html)
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 [http://secure.netroedge.com/~lm78/newdrivers.html](http://secure.netroedge.com/~lm78/newdrivers.html) for driver status.
##########

ACPI doesn't display ANYTHING reguarding fans, not even in boot notices.

pwmconfig reports:
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

acpi reports:
     Battery 1: charged, 100%
     Thermal 1: ok, 61.0 degrees C
  AC Adapter 1: on-line

My Laptop gets up to 70 C and I had to install an external fan to it to keep it sufficiently cool (58 C)

I've tried every howto in these forums, they always lead to one place-- Where do I get the proper modules as to install support since they aren't in the repos?

If these lack of support problems are not rectified, it COULD risk severe hardware damage.

---

### Post by lawentzel on 2007-03-29
Just a thought, have you looked in the BIOS to see if there is anything in there that allows it to control the cooling?  Usually from my experience, that is controlled by the BIOS and the hardware.  Thermal couple and such.

---

### Post by raffytaffy on 2007-03-29
if its single core you may want to turn SMP off. 

do a "uname -a" and if it has SMP in it..that could be it.

---

### Post by DigitalXeron on 2007-04-03
> **lawentzel said:**
> Just a thought, have you looked in the BIOS to see if there is anything in there that allows it to control the cooling?  Usually from my experience, that is controlled by the BIOS and the hardware.  Thermal couple and such.

BIOS control panel has nothing reguarding the fan.

> **raffytaffy said:**
> if its single core you may want to turn SMP off. 

do a "uname -a" and if it has SMP in it..that could be it.

SMP is already disabled.

---

### Post by ramjet_1953 on 2007-04-04
There is an applet that you can install on either the top or bottom taskbar called CPU Frequency Scaling Monitor. (Right-click on the task bar and a window will open, allowing you to choose the applet)

Install it and see if your CPU is scaling correctly. 

Quite often an overheating problem is caused by by the CPU running flat-out 100% of the time.

If your CPU is not scaling, we need to address that issue.

Regards,
Roger :cool:

---

### Post by DigitalXeron on 2007-04-04
> **ramjet_1953 said:**
> There is an applet that you can install on either the top or bottom taskbar called CPU Frequency Scaling Monitor. (Right-click on the task bar and a window will open, allowing you to choose the applet)

Install it and see if your CPU is scaling correctly. 

Quite often an overheating problem is caused by by the CPU running flat-out 100% of the time.

If your CPU is not scaling, we need to address that issue.

Regards,
Roger :cool:

Re: THe applet - is there anything KDE-based or is usable on the commandline?

I thought Celeron M processors didn't have scaling capabilities of their Pentium counterparts and were locked to the manufacturered processing power.

Last time I tried installing any scaling software, it said my processor did NOT support scaling.

---

### Post by jjordan on 2007-04-04
Celeron M does in fact support frequency scaling, it is running fine on my fujitsu P1510. What version of Ubuntu are you running.  I had to futz with Edgy for days to get scaling to work but Fiesty worked perfect on install.

- j

---

### Post by esaym on 2007-04-04
Does it overheat in windows?  70*c really isn't over heating for a laptop....  I would be worried if it was 90 or something.

---

### Post by psiu on 2007-04-22
Why do you think it's overheating? Is it unstable? Throttling back or shutting down? I may be new to Ubuntu, but as far as laptops are concerned, 70C is fine.

I have a nice old P3 here, and the fan is on *very low* until 70C. It then kicks up to approximately 50%, at 75C it will kick up to 66-75%, and at 80C it will go to 100% until it is back down to 75. Generally it will run itself back down to 50C and then throttle the fan back. Usually idles at about 65C or so. 

Laptop components are made and expected to run hotter. Fan speeds are usually hardcoded into the BIOS--this does NOT mean you will have anywhere to alter their settings.

And of course, the fans CAN go bad as well...is the little bugger blowing heat out?

---

### Post by dolphinsonar on 2007-04-27
My CPU is at 100% all the time, and the fan is on constantly.

Any ideas?

---

### Post by ezaton on 2007-04-27
Not really. Use 'top' to detect the misbehaving process, and kill it (if it's reasonable). 
All modern Intel M processors can scale up and down well. 
Using my own IBM X41, I try to avoid exceeding the 55C, but it might be that I can perform and maintain the system at a lower temperature.

DigitalXeron
Try using /proc/acpi to learn some about your system. You can safely cat any file in there to your standard output. Avoid 'cat'ing into them if you don't know what you're doing. You could obtain temp and fan performance from there, if from anywhere.

Ez

---

