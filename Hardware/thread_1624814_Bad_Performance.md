---
title: "Bad Performance"
date: 2010-11-18
forum: Hardware
---

### Post by NateN34 on 2010-11-18
Update: Installed 32 bit now and no difference from 32 bit. Just going to format the Linux partition stick to Windows 7. Linux  flash problems is a big killer for me, and I really had no point to use Linux, since Windows is more superior in compatibility ways.

---

### Post by SlugSlug on 2010-11-18
run 
```
top
```
in terminal and post output

---

### Post by NateN34 on 2010-11-18
> **SlugSlug said:**
> run 
```
top
```
in terminal and post output
```
nate34@Nate-HP-HDX16-Notebook-PC:~$ top

top - 09:41:08 up 51 min,  3 users,  load average: 1.25, 0.93, 0.75
Tasks: 166 total,   1 running, 165 sleeping,   0 stopped,   0 zombie
Cpu(s): 72.4%us,  7.7%sy,  0.0%ni, 18.8%id,  0.0%wa,  0.0%hi,  1.1%si,  0.0%st
Mem:   4026204k total,  1812304k used,  2213900k free,    69176k buffers
Swap:  2342908k total,        0k used,  2342908k free,   937348k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3283 nate34    20   0  341m 110m  18m S  125  2.8   0:42.91 npviewer.bin       
 1403 root      20   0  155m  51m  23m S   18  1.3   5:20.33 Xorg               
 2971 nate34    20   0  275m  24m  18m S   13  0.6   1:31.98 gnome-system-mo    
 3252 nate34    20   0  563m  89m  29m S    4  2.3   0:09.36 firefox-bin        
 1725 nate34    20   0  289m  56m  21m S    2  1.4   1:13.51 compiz             
 1730 nate34     9 -11  281m 5540 3892 S    2  0.1   0:09.74 pulseaudio         
 3011 nate34    20   0  315m  16m  11m S    1  0.4   0:01.47 gnome-terminal     
 1977 nate34    20   0  122m  30m 4480 S    0  0.8   0:05.55 ubuntuone-syncd    
 2435 nate34    20   0  327m  15m  11m S    0  0.4   0:01.28 cpufreq-applet     
 2655 nate34    20   0  538m  52m  26m S    0  1.3   0:56.63 chrome             
    1 root      20   0 23864 2028 1308 S    0  0.1   0:00.72 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.07 ksoftirqd/0        
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.15 ksoftirqd/1        

```
This is while running a HD Vid

---

### Post by SlugSlug on 2010-11-18
xorg may be a little high

> Sitting at idle on the desktop I am getting and average of 11.5% on the  first core and 11-17% on the second core, for CPU usage. Seems to be  very inconsistent.


can you post the top again but sitting at idle so we can see this 11% ?

---

### Post by NateN34 on 2010-11-18
> **SlugSlug said:**
> xorg may be a little high




can you post the top again but sitting at idle so we can see this 11% ?
Oops, well it seems to be 0%. I guess it says the 11% was coming from the system monitor tool.:oops:

---

### Post by NateN34 on 2010-11-18
> **NateN34 said:**
> Oops, well it seems to be 0%. I guess it says the 11% was coming from the system monitor tool.:oops:
EDIT: Still the flash performance is trash.

---

### Post by linux18 on 2010-11-18
use flash aid  for flash and consider lubuntu for a more lightweight distro

---

### Post by snowpine on 2010-11-18
Have you installed the drivers for your Nvidia graphics card?

---

### Post by iponeverything on 2010-11-18
gnome system monitor will keep a core at 10%. 

performance issues with flash have little to Ubuntu, as they exist on every other platform.

---

### Post by weblordpepe on 2010-11-18
Why is npviewer.bin running on its own? shouldnt it be inside firefox?

---

### Post by NateN34 on 2010-11-18
> **weblordpepe said:**
> Why is npviewer.bin running on its own? shouldnt it be inside firefox?
Well, I was running chrome at this time.

---

