---
title: "power now doesn't seem to work"
date: 2005-03-21
forum: Hardware &amp; Laptops
---

### Post by efbie on 2005-03-21
Hello !
I just installed ubuntu, on my aspire 1500 (amd64 3000) 
and everything works well, but i have a problem : the fan makes a lot of noise.

The only thing i installed so far is the ati drivers. 

the cpu speed applet shows crazy numbers
and if try to start powernowd here is what it says :

fred@Fred-Ubuntu:~ $ sudo su
root@Fred-Ubuntu:/home/fred # powernowd -u 50
powernowd: PowerNow Daemon v0.90, (c) 2003-2004 John Clemens
powernowd: Found 1 cpu:
Couldn't open file: No such file or directory
Couldn't open file: No such file or directory
Couldn't open file: No such file or directory
couldn't open govn's file for writing: No such file or directory
Couldn't get per-cpu data: Illegal seek
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.5/v2.6 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)
If all of the above are true, and you still have problems,
please email the author: [email]clemej@alum.rpi.edu[/email]

I hope there is a solution ! 
thank you :)

---

### Post by smtanner on 2005-04-07
I am having this same problem.  It was working but it quit working on april 5th or 6th.

---

### Post by SubZero_AK on 2005-04-08
I wanted to give this thread a bump as well.  My Dell 5150 laptop also doesn't seem to be able to use the powernowd.  I get the same error message as the first post.

Here is the output of my cat /proc/cpuinfo:

subzero@Icebox:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Mobile Intel(R) Pentium(R) 4     CPU 3.06GHz
stepping        : 9
cpu MHz         : 3056.961
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 6062.08


The CPU frequency scaling monitor doesn't even recognize my CPU.

Thanks in advance.

Mark

---

### Post by Nano on 2005-04-08
Same here with Medion 40100 laptop.

---

### Post by fizgig on 2005-04-08
@SubZero_AK:  I have the exact same processor.  I had to **modprobe p4-clockmod **to get it to work.  One easy way to see if you solve the problem is to** cat /proc/cpufreq **and see if you get any information. Before modprobing, you shouldn't get anything but after modprobing you will. After that, just restart powernowd (**sudo /etc/init.d/powernowd restart**)

edit:  If you want the module to happen each time you start you computer, add **p4-clockmod **to your /etc/modules file.  My [linux page]("http://www.mattsmith.hostmatrix.org/zx5078cl/") where I detail how I got Ubuntu working details this and others if you're interested.

---

### Post by SubZero_AK on 2005-04-08
Thank you, thank you....that took care of it and now my cpu is displayed and hopefully my system will run a little cooler.

Mark

---

### Post by fizgig on 2005-04-08
Glad I could help.  You might now want powernow to run **only** if the laptop's plugged in.  See [this post]("http://www.ubuntuforums.org/showthread.php?t=21370") if you want to make some simple changes to automatically start and stop powernow based on the state of the AC adaptor.

I did this since my cool screensavers look bad if powernow is running - lots of pauses.  After the modifications, all's well.

---

