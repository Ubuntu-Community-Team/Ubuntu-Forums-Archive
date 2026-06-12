---
title: "Powernowd and CPU always slow"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by EcliptuX on 2005-05-10
Hi,

I have a Compaq Presario R3410 laptop with and AMD Athlon XP 2800+ processor.
It's running at only 50% of it's speed (800MHz instead of 1600MHz), even when I'm running a big application.
The speed seems be fixed and powernowd seems not working very well :(

When I'm running this command, we can see the mistake :
 ```
root@Narayan:/home/ecliptux # cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 4
model name      : AMD Athlon(tm) XP Processor 2800+
stepping        : 10
cpu MHz         : 797.942
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 pni syscall nx mmxext 3dnowext 3dnow
bogomips        : 1581.05
``` 

What's the problem ?


PS : excuse me for my deplorable english :D

---

### Post by 23meg on 2005-05-10
try killing powernowd by typing "sudo killlal powernowd", and check your speed again. it doesn't have to be running when you're working with ac power. on batteries you may want to try [cpuspeedy](http://cpuspeedy.sourceforge.net/)  as an alternative.

---

### Post by EcliptuX on 2005-05-10
[QUOTE=23meg]try killing powernowd by typing "sudo killlal powernowd", and check your speed again. it doesn't have to be running when you're working with ac power. on batteries you may want to try [cpuspeedy]("http://cpuspeedy.sourceforge.net/")  as an alternative.[/QUOTE]
Hummm powernowd was not running:?
When I try to run it, I have :
 ```
root@Narayan:/home/ecliptux # /etc/init.d/powernowd start
Starting powernowd: required sysfs objects not found!
		Read /usr/share/doc/powernowd/README.Debian for more information.
```
So, I have look the readme file : 
 ```
 You just need
to ensure they are loaded (cpufreq_userspace, and on my system also 
speedstep_centrino).  One way to do this is to add them to /etc/modules, which
will cause them to load at boot time (see "man 5 modules").
```
I have inserted the line powernow-k7 to my /etc/modules
In the readme file, there is too :
 ```
**You also need to have the sysfs file system mounted**, so that the daemon can
find the interface to the frequency scaling support in the kernel.  If that
isn't already done, mkdir /sys and add an entry to /etc/fstab that looks 
something like this:

	sysfs /sys sysfs defaults 0 0

The entry that must be visible before powernowd can function is:

	/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

If that file isn't present, then the /etc/init.d/powernowd script will point 
you to this file instead of trying to launch the daemon...
``` 
So I have addedthe line "sysfs /sys sysfs defaults 0 0" in /etc/fstab and I reboot my laptop
I have an error when I try to go in /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
In fact, I have nothing in /sys/devices/system/cpu/cpu0/ !!!!
 ```
root@Narayan:/sys/devices/system/cpu/cpu0 # ll
total 0
``` 
](*,)

---

### Post by Arthemys on 2005-05-10
My older compaq had the same problem when I upgraded from ME to XP. Never sped up properly.

Try booting up with the AC plugged in, that could do it. I believe that's what I did to get it to work for me then.

---

### Post by EcliptuX on 2005-05-10
I had tried with or without AC plugged without success.
But under WinXP, the scalling of the processor works well !

---

### Post by Arthemys on 2005-05-10
I'm not entirely sure (when am I? ;) )

But it could be something that needs to be built into the kernel, a module perhaps to support the frequency scaling.

---

### Post by odix on 2005-05-11
Hello,
maybe [this thread](http://ubuntuforums.org/showthread.php?t=21370) will solve your problem. powernowd is an ondemand freq scaler, I think the default level for going up is about 80% cpu usage or so, "man powernowd" also helps

regards

---

### Post by EcliptuX on 2005-05-11
```
 But it could be something that needs to be built into the kernel, a module perhaps to support the frequency scaling.
``` 
Maybe.... :-|
But I don't understand why everybody have no problem with this AMD processor but me I have

[QUOTE=odix]Hello,
maybe [this thread]("http://ubuntuforums.org/showthread.php?t=21370") will solve your problem. powernowd is an ondemand freq scaler, I think the default level for going up is about 80% cpu usage or so, "man powernowd" also helps

regards[/QUOTE]
I try to use the scripts above but without success ](*,)

I think my problem is because I have nothing inside /sys/devices/system/cpu/cpu0
:roll:

---

### Post by EcliptuX on 2005-05-12
I have something new.
When I do a lshw, I have :
 ```
	 *-cpu
		  description: CPU
		  product: AMD Athlon(tm) XP Processor 2800+
		  vendor: Advanced Micro Devices [AMD]
		  physical id: 4
		  version: 15.4.10
		  slot: Socket A
		  size: 800MHz
		  capacity: 1600MHz
		  clock: 133MHz
``` 
...so, the system admit than my CPU could run at 1600MHz
I have hope:grin:

---

### Post by EcliptuX on 2005-05-12
Other clue :
 ```
#cat /proc/cpufreq
car: /proc/cpufreq: no file or no directory of this type
```

---

### Post by EcliptuX on 2005-05-13
up :)

---

### Post by EcliptuX on 2005-05-16
**Darktux, **a french guy find the soluce !!!!
Strangely, the Atlhon XP +2800 processor need these modules to be loaded :
powernow-k8
cpufreq_ondemand
cpufreq_userspace

You don't have to recompile the kernel !!!!

---

