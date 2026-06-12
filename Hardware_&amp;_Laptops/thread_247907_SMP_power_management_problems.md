---
title: "SMP power management problems"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by hizaguchi on 2006-08-31
I have a Turion X2 processor in my notebook.  If I use the default single core kernel, everything works fine.  The processor scales dynamically on demand and suspend to ram works flawlessly.  However, if I install any of the SMP kernels, both kernels are recognized but they never seem to scale down and I cannot resume from suspend to ram.  Is this a normal problem?  Is there a fix?

For reference, the closest I've ever come to fixing this was in Arch Linux.  There, using the powernow-k8 module (also used in Ubuntu) and powersaved (alto tried in Ubuntu), scaling and suspend work perfectly when I start the computer, but the powernow-k8 module loses control of the 2nd processor core after resuming from suspend.

Any clue what's going on here?

---

### Post by hizaguchi on 2006-08-31
Heh, I tried to install PC-BSD and it didn't like me.  Trying to suspend resulted in a short delay followed by the loudest, highest pitched screaming sound any computer speaker has ever made.  Guess I'll be continuing my search for a solution in Linux. :)

---

### Post by wasteed on 2006-09-01
I believe SMP and suspend/hibernate don't always play well together. There was a write-up about swsusp (suspend to disk) on the kernel mailing list recently ([http://kerneltrap.org/node/6878 ](http://kerneltrap.org/node/6878 ) ), which mentioned it needed more testing with SMP machines, and that was referring to a more recent kernel (2.6.18-rc2) than what we have installed with Dapper. 

Also, my previous posts here  [http://www.ubuntuforums.org/showthread.php?t=222921#4](http://www.ubuntuforums.org/showthread.php?t=222921#4)
report how well it works for me. Basically, sometimes it works, sometimes it doesn't - it tends to be OK if I power my laptop on then either suspend/hibernate almost straight away, but if I've been using it for any amount of time there's usually a problem on/after resuming and I have to reboot.

---

### Post by hizaguchi on 2006-09-01
Ah, so I'm basically screwed. :)  Thanks.

---

### Post by hizaguchi on 2006-09-01
Oh, one more thing.  Do you know if there is any danger in running the SMP kernel since it appears that the kernel isn't scaling the processors?  I wouldn't want to overheat my laptop or anything.  If it starts getting too hot, will the bios scale it down or something?

---

### Post by wasteed on 2006-09-01
I wouldn't know to be sure - my cpu frequency scaling just works! For my processor, lsmod shows it's using the speedstep_centrino kernel module. Not sure what yours should be. 

As for temperature issues, my laptop runs pretty well in that regard - don't really see it getting hot like others report; unless I'm playing nexuiz.. :)

---

### Post by hizaguchi on 2006-09-01
My scaling module is powernow-k8, and it's loading as it should, it just doesn't seem to be scaling the processors.  It changes the "bogomips" readings, but not the clock speeds.  I'm not sure what that's all about, but using the single core kernel both the "bogomips" and clock speed change.

I don't normally have temperature problems, but I worry that I'll set up the computer to do something processor-intensive and leave it alone for a while and come back to a slab of not-so-tasty bacon.

---

### Post by wasteed on 2006-09-01
Sounds like an issue with SMP doesn't it? Another random thought : have you installed cpufrequtils? There are a couple of useful tools: 

cpufreq-info   which summarises your cpu scaling properites (available frequencies, scaling governors)

cpufreq-set    which allows you to set the governor.

Maybe you can override it manually before you start doing CPU intensive
jobs?

For example, cpufreq-info shows the following for me :


analyzing CPU 0:
  driver: centrino
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1000 MHz - 2.16 GHz
  available frequency steps: 2.16 GHz, 1.66 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.16 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
analyzing CPU 1:
  driver: centrino
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1000 MHz - 2.16 GHz
  available frequency steps: 2.16 GHz, 1.66 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: frequency should be within 1000 MHz and 2.16 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.


And I'm user the "userspace" governor by default. One of my processors got stuck in performance after a suspend once, though I only managed to cure it with a reboot!

---

### Post by pharcyde on 2006-09-02
Did you load the cpufreq_* modules?  I have a K8 AMD smp kernel and mine is working.  I had the same problem as you before I loaded the following modules along with powernow-k8.

cpufreq_conservative
cpufreq_powersave
cpufreq_userspace     
cpufreq_ondemand
cpufreq_stats

You don't necessarily need to load them all just the ones you want.  After they have been loaded you need to configure the governor to use the one you want by modifying /sys/devices/system/cpu/[COLOR="Blue"]cpu0[/COLOR]/cpufreq/scaling_governor.  For the second core the configuration should be the same for cpu0 as the /sys/devices/system/cpu/[COLOR="Blue"]cpu1[/COLOR]/cpufreq directory should just be a symbolic link to the cpu0 directory.  There are loads of other configuration options in the directory that can be modified to your liking.

Also have a look at this link [http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by hizaguchi on 2006-09-02
Ah, I forgot about cpufreq-info.  It says my processors are scaled (in agreement with the  "bogomips" numbers), so I assume everything is working and /proc/cpuinfo is incorrect.  Thanks!  Now if suspend would just work. :)

Is that K8 kernel 64-bit?  Because I'm running 32-bit Dapper and I can't find anything newer than K7.  I didn't have any luck suspending in 64-bit either, but I'm still curious. :)

---

### Post by hizaguchi on 2006-09-02
HAHA!  It works in Edgy knot 2!  Everything works!  Out of the box!  Sweet!

---

