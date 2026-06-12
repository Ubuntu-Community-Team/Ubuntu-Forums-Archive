---
title: "HOWTO: Use cpufreqd to manage CPU scaling"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by muzzz on 2007-03-27
NOTE: While this guide was written for, and tested with, a Pentium M, it should be fairly straightforward to adapt it to other processors which work with cpufreq.

Tested with
[LIST]
[*]NEC Versa P520 notebook
[*]Intel Pentium M 1.4Ghz processor
[*]Kubuntu 6.10
[*]2.6.17-11-generic kernel
[/LIST]

By default, Ubuntu uses the powernowd daemon to manage CPU frequency scaling. This daemon directly sets the CPU frequency based on system load, using the userspace governor. Allegedly, this is a rather inneficient way to manage CPU frequency scaling. A better way seems to be to use the kernel cpufreq governor modules (see [http://ubuntuforums.org/showthread.php?t=248867)](http://ubuntuforums.org/showthread.php?t=248867)).

While the cpufreq modules provide a very nice interface, I still found it lacking in flexibility. Most notably I missed a way to dynamically change governors based on, for example, battery status. To solve this, I switched to cpufreqd.

Contrary to powernowd and many other CPU scaling daemons, cpufreqd does not run in userspace. It simply configures the cpufreq governors according to rules you supply. You can switch modes according to battery status, system load, etc., etc.. It even allows you to switch modes when running certain programs (hint: your favourite movie player).

Switching from powernowd to cpufreqd involves a number of steps:

**Step 1: Removing powernowd**
Use your preferred package manager to remove powernowd, or open a terminal and do
```
sudo apt-get remove powernowd
```
If you've installed any other CPU scaling programs it will probably be best to remove them as well.

**Step 2: Install cpufreqd**
Use your preferred package manager to install cpufreqd, or open a terminal and do
```
sudo apt-get install cpufreqd
```
**NOTE**: cpufreqd resides in the Universe repository. You may have to enable Universe before being able to install cpufreqd.

**Step 3: Reboot**
To test if cpufreqd is actually installed correctly a reboot is usually required

**Step 4: Check if it worked**
Open a terminal and do
```
ps -A | grep cpufreqd
```
This should output a line ending with "cpufreqd" (without quotes), showing that cpufreqd is up and running

**Troubleshooting**
On my system, cpufreqd failed to start after the reboot. Some (mod)probing around showed that the necessary kernel modules had not been loaded. Apparantly the default install of cpufreqd assumes that it does not need to load the CPU kernel module. To solve this do:
```
sudo nano /etc/default/cpufreqd
```
Locate the following line
```
CPUFREQ_CPU_MODULE=""
```
and change it tp
```
CPUFREQ_CPU_MODULE="speedstep-centrino"
```
**NOTE**: if you're using a non-speedstep scaling-capable processor you'll probably have to specify a different module here. [http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867) has some hints for determining which module you need.

Save the file and reboot.

You should now be ready to start configuring cpufreqd to your needs. I found configuration fairly straightforward and well documented, so I'll leave that step to you. For more information, try
```
man cpufreqd
cat /etc/cpufreqd.conf
```

Enjoy!

---

### Post by nachotronics on 2007-03-29
An easy way to control this is to install emifreq-applet wich allows you to scale the processor speed or set automatic scaling from your task bar, you need to start the emifreqd (emifreq daemon) at startup for it to work by adding "sudo emifreqd" to System - Preferences - Sessions - Startup

Hope this helps :wink:

---

### Post by jgordon510 on 2007-04-20
My system used to overheat when doing processor intensive tasks.  After doing this, it runs cool.  I had to come back and find this post again because upgrading to feisty reversed this change.

---

### Post by jakala on 2007-04-24
Good tip, it work well on my laptop (HP NW8000) with feisty, I just need to  add the EmiFreq icon manually.

---

### Post by eidam655 on 2007-11-10
wow, good how-to...

but i have little problem: i don't have pentium m, but Celeron M... and so, when i do the step 4, it says nothing :(

or is it because i'am using gutsy? or why? because when i do 'cpufreq-info' it says that an unknown driver handles my processor...

what can be the problem?

---

### Post by phelin4 on 2007-11-10
> **eidam655 said:**
> wow, good how-to...

but i have little problem: i don't have pentium m, but Celeron M... and so, when i do the step 4, it says nothing :(

or is it because i'am using gutsy? or why? because when i do 'cpufreq-info' it says that an unknown driver handles my processor...

what can be the problem?

Maybe the fact that Celerons do not support frequency scaling?

---

### Post by fhqwhgad on 2007-11-12
I'm having a little trouble getting cpufreqd to start up at boot.
I have a Centrino CPU.
/proc/cpuinfo: model name      : Intel(R) Pentium(R) M processor 1.60GHz

When i try to modprobe the centrino, this is what i get:
nicolai@obscure:~$ sudo modprobe speedstep-centrino
/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device
nicolai@obscure:~$

Am i doing something wrong?

---

### Post by eidam655 on 2007-11-13
> **phelin4 said:**
> Maybe the fact that Celerons do not support frequency scaling?

yes, but:

in my Windows, asus has installed there an utility called Power4Gear, which downclocks or overclocks the CPU (it probably changes only the cpu mulitplier), due to selected profile.

is there any chance of getting similar utility for linux as well?

thx

---

### Post by spupy on 2007-11-28
> **eidam655 said:**
> wow, good how-to...

but i have little problem: i don't have pentium m, but Celeron M... and so, when i do the step 4, it says nothing :(

or is it because i'am using gutsy? or why? because when i do 'cpufreq-info' it says that an unknown driver handles my processor...

what can be the problem?

I have Celeron M on my toshiba laptop. Under Windows there is an utility from toshiba to scale the cpu frequency. Under linux i made it work 10 minutes ago ;) Read this [http://ubuntuforums.org/showthread.php?t=582069]("http://ubuntuforums.org/showthread.php?t=582069")

---

### Post by phelin4 on 2007-12-17
> **spupy said:**
> I have Celeron M on my toshiba laptop. Under Windows there is an utility from toshiba to scale the cpu frequency. Under linux i made it work 10 minutes ago ;) Read this [http://ubuntuforums.org/showthread.php?t=582069]("http://ubuntuforums.org/showthread.php?t=582069")

Celeron M's do not scale their frequency. They might throttle down though, meaning that the CPU will still run at 100% frequency but just sleep a part of it. This will result in slowed down performance, and somewhat (minimally compared to Pentium M/Core CPUs) lesser heat output, but no better battery life.

---

### Post by Ugljesa Jovanovic on 2008-03-16
I  wrote a really simple shell script for managing cpufreq, maybe someone will find it useful [www.IonSpin.net]("http://www.ionspin.net/?q=node/8"). Note that it was tested on AMD, and on Gentoo, but it should work fine on ubuntu.

---

### Post by excogitation on 2008-03-22
Can't you use "CPU Frequency Scaling Monitor" (standard applet) to do that?

---

