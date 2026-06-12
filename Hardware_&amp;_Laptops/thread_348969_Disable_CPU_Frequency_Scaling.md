---
title: "Disable CPU Frequency Scaling"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by wiz561 on 2007-01-29
Hi!

    Simply put, how do you disable CPU Frequency Scaling?  I've looked for "powernowd", and nothing power<anything> exists in the init.d.  Everything I see says to stop powernowd from loading or cpuspeedy.  

   The reason why I ask is because I'm getting some "Firmware Unresponsive" errors with my Hauppauge PVR-150 TV Capture Card.  The friendly folks over at ivtv users' list said to...

...
Try disabling cpu frequency scaling. Look for daemons like cpuspeedy and
powernowd and disable them. This is most likely the cause of this problem.
...

     Right now, I have nosmp noapic set in my menu.lst, and this fixes the problem.  But now, I loose my second processor.  (I have a AMD Dual-Core processor.) 

     Just wondering how to disable this if the service doesn't exist in init.d.


Thanks,
Mike

---

### Post by Paerez on 2007-01-29
post the output of:
```
ls /etc/init.d
```

---

### Post by K.Mandla on 2007-01-29
There are different cpu scalers for different hardware; I'm not sure what the AMD series uses, but you might look for *cpufreq* or *cpudyn* as well. 

It might also be an option in your BIOS to disable cpu scaling. Again, I'm not sure that would solve the problem, but it is something of a trump card for frequency throttling ... if you have it, that is. :roll:

---

### Post by wiz561 on 2007-01-29
Here is the output for /etc/init.d

root@chorizo:/home/wisniewski# ls -l /etc/init.d/
total 292
-rwxr-xr-x 1 root root 9342 2006-07-30 20:51 alsa-utils
-rwxr-xr-x 1 root root  969 2006-07-20 21:40 atd
-rwxr-xr-x 1 root root 3597 2006-10-06 06:37 bootclean
-rwxr-xr-x 1 root root 2121 2006-10-06 06:37 bootlogd
-rwxr-xr-x 1 root root 1883 2006-10-06 06:37 bootmisc.sh
-rwxr-xr-x 1 root root 2887 2006-10-06 06:37 checkfs.sh
-rwxr-xr-x 1 root root 9875 2006-10-06 06:37 checkroot.sh
-rwxr-xr-x 1 root root 6211 2006-09-07 17:36 console-screen.sh
-rwxr-xr-x 1 root root  680 2006-09-22 10:53 console-setup
-rwxr-xr-x 1 root root 1741 2006-07-20 21:38 cron
-rwxr-xr-x 1 root root  795 2006-06-28 18:59 dns-clean
-rwxr-xr-x 1 root root 6177 2006-10-10 08:27 glibc.sh
-rwxr-xr-x 1 root root 1228 2006-10-06 06:37 halt
-rwxr-xr-x 1 root root 5137 2005-04-21 05:10 hdparm
-rwxr-xr-x 1 root root  909 2006-10-06 06:37 hostname.sh
-rwxr-xr-x 1 root root 3634 2006-10-12 10:47 hwclock.sh
-rwxr-xr-x 1 root root  493 2006-09-22 10:53 keyboard-setup
-rwxr-xr-x 1 root root  944 2006-10-06 06:37 killprocs
-rwxr-xr-x 1 root root 1928 2006-10-06 08:47 klogd
-rwxr-xr-x 1 root root  349 2007-01-09 02:48 linux-restricted-modules-common
-rwxr-xr-x 1 root root 3382 2006-07-10 13:16 lirc
-rwxr-xr-x 1 root root  748 2006-01-23 12:47 loopback
-rwxr-xr-x 1 root root 1053 2006-07-20 21:08 makedev
-rwxr-xr-x 1 root root 1234 2006-07-04 21:02 module-init-tools
-rwxr-xr-x 1 root root  617 2006-10-06 06:37 mountall-bootclean.sh
-rwxr-xr-x 1 root root 2354 2006-10-06 06:37 mountall.sh
-rwxr-xr-x 1 root root 1491 2006-10-06 06:37 mountdevsubfs.sh
-rwxr-xr-x 1 root root 1087 2006-10-06 06:37 mountkernfs.sh
-rwxr-xr-x 1 root root  615 2006-10-06 06:37 mountnfs-bootclean.sh
-rwxr-xr-x 1 root root 2689 2006-10-06 06:37 mtab.sh
-rwxr-xr-x 1 root root 6128 2006-10-11 18:43 mysql
-rwxr-xr-x 1 root root 2051 2006-10-11 18:43 mysql-ndb
-rwxr-xr-x 1 root root 1980 2006-10-11 18:43 mysql-ndb-mgm
-rwxr-xr-x 1 root root 2234 2007-01-27 11:24 mythbackend
-rwxr-xr-x 1 root root 1685 2006-07-03 14:12 networking
-rwxr-xr-x 1 root root  860 2005-10-28 21:48 nvidia-kernel
-rwxr-xr-x 1 root root 2302 2006-07-20 20:10 pcmciautils
-rwxr-xr-x 1 root root  345 2006-07-10 14:17 pppd-dns
-rwxr-xr-x 1 root root 1226 2006-09-08 10:37 procps.sh
-rwxr-xr-x 1 root root 8197 2006-10-06 06:34 rc
-rwxr-xr-x 1 root root  522 2006-10-06 06:37 rc.local
-rwxr-xr-x 1 root root  117 2006-10-06 06:34 rcS
-rw-r--r-- 1 root root 1335 2006-10-06 06:34 README
-rwxr-xr-x 1 root root  692 2006-10-06 06:37 reboot
-rwxr-xr-x 1 root root 1000 2006-10-06 06:37 rmnologin
-rwxr-xr-x 1 root root 3417 2006-07-20 21:09 rsync
-rwxr-xr-x 1 root root  452 2006-10-30 22:09 screen
-rwxr-xr-x 1 root root  755 2006-10-06 06:37 sendsigs
-rwxr-xr-x 1 root root  585 2006-10-06 06:37 single
-rwxr-xr-x 1 root root 4215 2006-10-06 06:37 skeleton
-rwxr-xr-x 1 root root 2016 2006-10-05 04:47 ssh
-rwxr-xr-x 1 root root  510 2006-10-06 06:37 stop-bootlogd
-rwxr-xr-x 1 root root  647 2006-10-06 06:37 stop-bootlogd-single
-rwxr-xr-x 1 root root 1804 2006-10-06 08:47 sysklogd
-rwxr-xr-x 1 root root 2584 2006-10-16 23:05 udev
-rwxr-xr-x 1 root root 3477 2006-10-06 06:37 umountfs
-rwxr-xr-x 1 root root 1833 2006-10-06 06:37 umountnfs.sh
-rwxr-xr-x 1 root root 1105 2006-10-06 06:37 umountroot
-rwxr-xr-x 1 root root 1815 2006-10-06 06:37 urandom
-rwxr-xr-x 1 root root 1939 2006-10-06 06:37 waitnfs.sh
-rwxr-xr-x 1 root root 1895 2006-08-11 12:30 wpa-ifupdown
-rwxr-xr-x 1 root root 1832 2006-09-10 09:21 x11-common
root@chorizo:/home/wisniewski#

---

### Post by RandomJoe on 2007-01-30
I'm assuming you are running Edgy, since 'powernowd' isn't running (that's what does the scaling in Dapper).  Edgy is using one of the built-in kernel modules (cpufreq_ondemand) to handle the scaling by default.

The available governors can be seen if you run:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```
For that matter, you can see which one is active with:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
'Userspace' means a daemon like powernowd does the scaling.

The quick-and-easy way to stop that is (as root):
```
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

I just checked on mine, and if you have a dual-core proc you need to do this separately for each core - so change 'cpu0' to 'cpu1' for the second.  (Rather weird to see each core at a different frequency...!)

The 'performance' governor just leaves the CPU at full speed.

If you want a more permanent solution, I would just add the above line to a boot script.

---

### Post by wiz561 on 2007-01-30
I tried this with the nosmp and noapic values set in menu.lst...maybe I should give this a shot before asking this question...

But with the 'echo /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors' command, doesn't it just echo that path and don't I want to use 'cat' instead?

EDIT: Updated...  I tried to do the above but this doesn't exist...

root@chorizo:/home/wisniewski# echo /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
----
root@chorizo:/home/wisniewski# ls -l /sys/devices/system/cpu/cpu0/
total 0
-r-------- 1 root root 4096 2007-01-30 10:52 crash_notes
drwxr-xr-x 2 root root    0 2007-01-30 10:50 topology
----
root@chorizo:/home/wisniewski# ls -l /sys/devices/system/cpu/cpu0/topology/
total 0
-r--r--r-- 1 root root 4096 2007-01-30 10:53 core_id
-r--r--r-- 1 root root 4096 2007-01-30 10:53 core_siblings
-r--r--r-- 1 root root 4096 2007-01-30 10:53 physical_package_id
-r--r--r-- 1 root root 4096 2007-01-30 10:53 thread_siblings
root@chorizo:/home/wisniewski# 
----

Thanks!

---

### Post by K.Mandla on 2007-01-30
I believe that path is created when the *cpufreqd* package is installed, and the proper speedstep module is inserted. Until then, I don't think it's going to show anything. ...

---

### Post by RandomJoe on 2007-01-30
> **wiz561 said:**
> But with the 'echo /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors' command, doesn't it just echo that path and don't I want to use 'cat' instead?

EDIT: Updated...  I tried to do the above but this doesn't exist...

Duh...  Yes, those first two should be 'cat'!  So much for proofreading...!

Interesting - if you don't have a cpufreq directory in the cpu0 directory, then the modules aren't loading.  Something else is doing the scaling.  I've never seen that before!

---

### Post by Theimon on 2007-01-30
Maybe you got CoolnQuiet enabled in BIOS, or check the BIOS power management settings. Since you can't find anything particular among daemons etc.....

---

### Post by wiz561 on 2007-01-30
Interesting, leave it to me to make things strange!

I went into the bios and disabled all the 'power management' things that I could find.  Cool 'n' Quiet was not one of them though.  But there was a 'power management' menu, which everything is now disabled.

Interesting enough though, if I cat /proc/cpuinfo, I get the usual....2 processors, all the stats...  But the very last line says "power management".  Somehow, I wonder if this is the key to it.  

Oh, and also, yes, I am running Ubuntu 6.10.

Thanks for everybody's help...

---cut of one processor----
processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 2
cpu MHz         : 2211.392
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 4422.90
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

---

