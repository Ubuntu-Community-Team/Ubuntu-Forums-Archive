---
title: "lm-sensors..w83627ehf"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by MrGreen on 2007-04-26
Hi,

sensors detect states I need w83627ehf only modprobe will not work module not found ;-S looked in hwmon and its there

Am I missing something?

---

### Post by stephenhorgan on 2007-04-26
Are you sure it shouldn't be the w83627hf module? I have the following modules loaded for my lmsensors setup:
<code>
Module                  Size  Used by
w83627hf               25360  0 
hwmon_vid               3328  1 w83627hf
i2c_isa                 5248  1 w83627hf
eeprom                  7312  0 
i2c_dev                 7556  0 
</code>

---

### Post by ahaslam on 2007-04-26
if in doubt check your kernel config

---

### Post by MrGreen on 2007-04-27
FATAL: Error inserting w83627hf (/lib/modules/2.6.20-15-generic/kernel/drivers/hwmon/w83627hf.ko): No such device


Am I missing something ?

---

### Post by MrGreen on 2007-04-29
To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 0 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 1:00.0
i2c-i801
# Chip drivers
eeprom
w83627ehf
#----cut here----


Do you want to add these lines to /etc/modules automatically? (yes/NO)no
mrgreen@ubuntu:~$ sudo modprobe w83627ehf
FATAL: Error inserting w83627ehf (/lib/modules/2.6.20-15-generic/kernel/drivers/hwmon/w83627ehf.ko): No such device
mrgreen@ubuntu:~$ 


Output from sensors-detect it finds sensors but I cannot load them into kernel?

I would like to monitor my temps ... as I overclock my system 

Any Kernel gurus out there just point me in the right direction 

Thanks 

MrG

---

### Post by PhotoJoe on 2007-04-29
Try this tutorial. It worked perfectly for me. 

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

I have several old 'Frankenstein'  machines- some of the parts literally came from the junkyard. This has been a great tool to get some warning on voltages, temps, fan speed, etc. It's like having gauges in your car instead of idiot lights.  

Good Luck!

---

### Post by MrGreen on 2007-04-29
followed install in [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) just that modules are not in my kernel but they are in hwmon ??? 

Worked ok under.... wondered if headers are missing ?

---

### Post by nss0000 on 2007-04-29
AFAIK :: Some newer mobos/chipsets/cpus are not yet supported by LM-Sensors. In addition, the version of LMS that supports SOME newer mobos is not yet downloadable in binary, so must be compiled. 

nss
******

---

### Post by MrGreen on 2007-04-29
Thanks for the heads up .... wonder if its in beyond ;-)

---

### Post by Reinhardt on 2007-04-29
Do you have a newer Asus motherboard by chance - I am having the same problem with an Asus P5B Premium.   Lm-sensors.org lists w83627ehf driver support (for the Winbound W83627DHG chipset) in the new 2.6.21 kernel.   Is there any way to get this working in the 2.6.20-15 Feisty kernel??  Upgrading kernels would lead to tons of problems for a Linux newbie like myself.

---

### Post by MrGreen on 2007-04-30
Yes I am running a P5B ;-) ... to get my sensors working under Arch I had to rebuild with a patch to start with then they added it in .. to stock kernel [again as a patch!] 

As you say rebuilding on every update is a pain.....

I am surprised because I had no end of problems with my dvd drive when I first built this system [jmicron] 

So lm-sensors is more up to date than Ubuntu if you look in /lib/modules/2.6.20-15-generic/kernel/drivers/hwmon/ what do you see ?

Only tiny issue I have at the moment

---

### Post by Reinhardt on 2007-04-30
> **MrGreen said:**
> Yes I am running a P5B ;-) ... to get my sensors working under Arch I had to rebuild with a patch to start with then they added it in .. to stock kernel [again as a patch!] 

As you say rebuilding on every update is a pain.....

I am surprised because I had no end of problems with my dvd drive when I first built this system [jmicron] 

So lm-sensors is more up to date than Ubuntu if you look in /lib/modules/2.6.20-15-generic/kernel/drivers/hwmon/ what do you see ?

Only tiny issue I have at the moment


I have the w83627ehf.ko driver in my ubuntu Fiesty kernel, but it is the older driver that lacks W83627DHG support.   The support for the DHG chipset was added in mid-February to the driver.  Hopefully, a patch will be released specifically for the HWMON drivers or a backport for Fiesty with all the .21 kernel upgrades.  The actual driver in .c format can be obtained from [here](http://git.kernel.org/?p=linux/kernel/git/stable/linux-2.6.21.y.git;a=commit;h=657c93b10fac97467cdf1d0424a209ce2e81991a) after clicking on driver and selecting RAW, but it doesn't do me much good - not sure if that can be adapted to a patch?

---

### Post by tassoman on 2007-06-09
I'm stuck with a simple PB5 mobo. Just today i've upgraded to kernel 2.6.20-16 but still the same.

---

