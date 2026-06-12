---
title: "[SOLVED] Problems with cpufreq"
date: 2008-05-22
forum: Hardware
---

### Post by Doc Hoss on 2008-05-22
My laptop is running 7.04 and I'm having problems with the system stuttering every 30 or so seconds when I'm doing multiple tasks.  After checking the system log I found that cpufreq is running into some problems.

```
May 22 11:53:36 XXX-laptop kernel: [391205.548000] cpufreq: change failed with new_state 1 and result 0
May 22 11:53:43 XXX-laptop kernel: [391211.676000] cpufreq: change failed with new_state 0 and result 0
May 22 11:53:45 XXX-laptop kernel: [391212.692000] cpufreq: change failed with new_state 1 and result 0
```

This happens repeatedly.  I'm a little too much of a noob to start digging in and messing with something like cpufreq without a little guidance, so if anyone can help out, I'd appreciate it!

Edit: This happens in both Gnome and XFCE.

---

### Post by Doc Hoss on 2008-05-23
Quick bump here.  Anyone have ideas?

---

### Post by prshah on 2008-05-25
> **Doc Hoss said:**
> 
```
May 22 11:53:36 XXX-laptop kernel: [391205.548000] cpufreq: change failed with new_state 1 and result 0

```


Which CPU are  you using? What scaling governor are you using, and can use? ACPI status? The following commands will give you the information```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
cat /proc/cpuinfo
```

Post the information here, it will give much needed clues.

---

### Post by Doc Hoss on 2008-05-25
Thanks a lot for your reply...this is driving me insane, and yesterday I have a feeling it contributed to a couple of system lockups.  Here's the output from those commands....

...and also, if you don't mind, could you explain to me what each of those commands is doing?  I'm eager to really LEARN Linux rather than just be able to plug in commands as I'm told to.  Thanks in advance!

```
XXX@XXX-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
userspace powersave ondemand conservative performance

XXX@XXX-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
userspace

XXX@XXX-laptop:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 10
cpu MHz         : 600.000
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips        : 1203.74
clflush size    : 32


```

Thanks again!

---

### Post by Doc Hoss on 2008-05-30
Can anybody help on this?  I'd really appreciate it if I could get some insight into what could be causing this problem...or maybe how to fix it!  :)

---

### Post by Doc Hoss on 2008-06-05
Anyone able to come up with some sort of solution or workaround for this?  I'm really getting frustrated with Ubuntu's performance, since Windows doesn't do this.  Anyone have any idea how I can stop this?

---

### Post by prshah on 2008-06-10
> **Doc Hoss said:**
> 
...and also, if you don't mind, could you explain to me what each of those commands is doing?
```
XXX@XXX-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
userspace powersave ondemand conservative performance

XXX@XXX-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
userspace

XXX@XXX-laptop:~$ cat /proc/cpuinfo
model name      : Pentium III (Coppermine)
stepping        : 10
cpu MHz         : 600.000

```



OK I have not been able to see a Pentium III coppermine machine so I can't say this for sure: but I believe that you are facing problems because your scaling governor is userspace; for which you need certain utilities. I am also not sure if your processor supports cpu scaling or any other other governors.

Here a pointer to more information: [http://xlife.zuavra.net/index.php/70/](http://xlife.zuavra.net/index.php/70/)
This will also explain the commands you have run before.

Hope it helps. Post back if you have any questions.

---

### Post by Doc Hoss on 2008-06-16
Thank you for the info and the link.  They are both very helpful.  I've changed to the "performance" scaling governor.  Seems to be doing ok now, but is this the best setting for a laptop?  I've read elsewhere on the forums that it could be quite wasteful...and maybe shorten cpu lifespan?  Any truth to this that you are aware?

---

### Post by prshah on 2008-06-16
> **Doc Hoss said:**
> I've changed to the "performance" scaling governor.  
I've read elsewhere on the forums that it could be quite wasteful...and maybe shorten cpu lifespan?  Any truth to this that you are aware?

Can't be sure of the validity of that statement. However, I would suggest you use ondemand if possible.

---

### Post by Doc Hoss on 2008-06-19
I would use ondemand, but when I try to switch to it, I get this error...

```
Jun 19 15:45:01 XXX-laptop kernel: [   86.212000] ondemand governor failed to load due to too long transition latency
```

Any ideas why?

---

### Post by sdennie on 2008-06-19
That means that your CPU doesn't change frequencies fast enough to make ondemand a reasonable setting.  I would stick with "performance" for that particular chip.

---

### Post by Doc Hoss on 2008-06-21
Blasted old computer!  Oh well...can't beat it for the price I paid.......hooray for hand-me-downs!  :D  

Thanks for all your help guys.  I'll mark this one solved!

---

