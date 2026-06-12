---
title: "Heat problems with Laptop"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by bo_jo on 2007-03-21
I am new to Ubuntu and I am trying to run v. 6.10 on my laptop
(Compaq presario v6000z).  The heat is so excessive that I don't
even want to leave the laptop running too long trying to poke
around with settings. (core temp 58c, gpu temp 74c)
I can hear the fan go on and off sporadically and for short periods 
of time but I need to find a way to manage this heat issue.  I have
searched the forums for terms "acpi" "heat" "fans" etc but came up 
with too many posts to read through to find something relevant.
Under proc/acpi/thermal-zone/THERM/  I find a number of files,
cooling mode,polling,state,temperature,trip points etc. and
all of these files are empty, no contents.
Can someone point me to and set of instructions on managing
heat/fan settings in Ubuntu?
Thanks

---

### Post by srt4play on 2007-03-21
Is frequency scaling working?  

Right-click your panel -> add to panel -> cpu frequency scaling monitor

---

### Post by bo_jo on 2007-03-21
> **srt4play said:**
> Is frequency scaling working?  

Right-click your panel -> add to panel -> cpu frequency scaling monitor

Cpu scaling is enabled.

Another problem I found, some posts on this subject talk about editing 
a file called /proc/acpi/fan/fanx/state.  My folder /proc/acpi/fan is empty.
There are no subfolders or files.

---

### Post by bo_jo on 2007-03-21
I searched a little more and found a suggestion to disable acpi and apm at 
bootup.  This has forced the fan on but it disables cpu scaling and I cannot 
read the core temperature anymore.  The gpu temperature has decreased
a few points, but I don't know of disabling acpi is worth it.
Does anyone know of a way that I can trigger the fans to come on at a 
certain temperature level?
As I mentioned earlier, all of the files in proc/acpi/thermal-zone/THERM, which
I assume to be configuration files, are empty. I would like to find documentation
about what to put in those files to enable fan control at certain temperatures.

---

### Post by bo_jo on 2007-03-21
I made the original post because of my concern for my laptop
operating temperatures.  With only using desktop computers
in the past, I am accustomed to cpu temperatures in the high 
30c range and gpu temperatures in the low 40c range. 
Are temperatures (idle) of around 58-60c core and around 
74-75c gpu usually considered within an acceptable
range for a small laptop?

---

### Post by hardyn on 2007-03-21
55-60 and 60-70 on the GPU with my machine is normal for both windows and ubuntu for me with a PM based machine.

i have found the OSS video drivers to be quite inefficient, which driver are you using?  they seem to have been designed to run unthrottled for desktop use, and have little thought into notebook use.

one thing i would like you do...  what is the idle CPU usage of your machine?
what processor does your machine have?

---

### Post by bo_jo on 2007-03-21
> **hardyn said:**
> 55-60 and 60-70 on the GPU with my machine is normal for both windows and ubuntu for me with a PM based machine.

i have found the OSS video drivers to be quite inefficient, which driver are you using?  they seem to have been designed to run unthrottled for desktop use, and have little thought into notebook use.

one thing i would like you do...  what is the idle CPU usage of your machine?
what processor does your machine have?


The drivers are the Nvidia 1.0-9755 Linux IA32 drivers.

I have a 1.8ghz AMD sempron that idles at 800 mhz when acpi/cpu scaling is enabled.

---

### Post by hardyn on 2007-03-21
while the GPU might be a tad on the high side, the GPU is normal... i believe the thermal spec for that processor is like 95c, it is for the PMs anyway.

is the macine new new, or a bit oldish? give it a blast with some compressed air?

---

### Post by bo_jo on 2007-03-21
> **hardyn said:**
> while the GPU might be a tad on the high side, the GPU is normal... i believe the thermal spec for that processor is like 95c, it is for the PMs anyway.

is the macine new new, or a bit oldish? give it a blast with some compressed air?


The laptop is three weeks old

---

### Post by bo_jo on 2007-03-21
I am now trying to install lm-sensors. After using the guide here
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_control_fan_speed_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_control_fan_speed_.28lm-sensors.29)
I keep getting this error message:


Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!


Does anyone know of any comprehensive guide to installing lm-sensors 
that include sysfs and libsensors?

---

### Post by Brendantb on 2007-03-23
Hi, 

I find the greatest problem with linux isn't the lack of information, but that there is so much of it, scattered all over the place... :) 

Here is a guide to lm-sensors: 

[http://www.lm-sensors.org/wiki/FAQ](http://www.lm-sensors.org/wiki/FAQ)

If you follow chapter 2 closely, your machine should configure itself correctly: 

[http://www.lm-sensors.org/wiki/FAQ/Chapter2](http://www.lm-sensors.org/wiki/FAQ/Chapter2)

You can download X Sensors, which is a useful GUI app for displaying CPU temp on the Desktop.

---

### Post by MacDoogle on 2007-03-27
I am having a similar problem with a similar laptop. I have a Compaq Presario V3200.
After installing Ubuntu and then installing Nvidia drivers i noticed the GPU was getting temps of 89 and over when running glx gears. My CPU felt really hot, i didn't check the temp though. I was just wondering if you have solved the problem you had?

---

### Post by wrycatcher on 2007-03-30
I found a wealth of information (and history) here:

[https://launchpad.net/ubuntu/+bug/22336]("https://launchpad.net/ubuntu/+bug/22336")

Seems this bug just lingers on and on with no official solution.  Some folks managed to resolve it, but also sounds like a few have not been able to.  Out of the box, it seems Ubuntu might not be *one size fits all*, if that were even possible.  But Ubuntu does seem to cast the larger net in terms of the technical ability range of its users.  Something as potentially disasterous as insufficient/flawed cooling will severely hinder the adoption rate of Ubuntu...even if it totally rocks in most other aspects.  This is a deal-breaker for most people because of the risk of hardware damage.

---

